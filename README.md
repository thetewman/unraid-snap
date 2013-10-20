SNAP for unRAID Server
======================

Snap: Share Non-Array Partitions 

Add storage devices to an unRAID server without them being part of the unRAID array. Adding a device to SNAP means that it's filesystem will be mounted to make it available in linux and shared out to make it available on the network. SNAP is aware of the unRAID array drives and doesn't disturb any drives assined to the array. 


SNAP Installation
=================

To install SNAP you need to download the snap.plg and put it in the /boot/config/plugins directory.  You can download the file directly from GitHub and then browse to your flash drive and copy it to the /config/plugins directory or use a telnet session to download the file directly from GitHub with wget.  To install the plugin file, use a telnet session to your server, log in to the server, and then issue the following commands:

cd /boot/config/plugins

wget --no-check-certificate https://github.com/dlandon/unraid-snap/raw/master/snap.plg

Reboot your server

or

installplg snap.plg

SNAP will install.


NTFS Write Driver
=================

Before you install this plugin, delete any ntfs-3g packages from the /boot/extra directory otherwise you could end up with multiple package versions.  I know this is messy, but until unRAID package management is sorted out, this is the best I can do.

If you are using NTFS disk drives and need to write on them, you will need the ntfs-3g driver installed.  unRAID only supports reading from NTFS devices.  To enable NTFS write capability, do the following:

cd /boot/config/plugins

wget --no-check-certificate https://github.com/dlandon/unraid-snap/raw/master/ntfs-3g.plg

Reboot your server.

or

installplg ntfs-3g.plg

This will install the ntfs-3g package.


Revision History
================

Version 5.10 - Initial release.

Version 5.11 - Fixed drive busy detection and some unmount problems.

Version 5.12 - Fixed mount and unmount of disks with multiple partitions. SNAP should only mount the first partition on the disk.

Version 5.13 - Minor UI issues.

Version 5.14 - SNAP drives are now unmounted when the unRAID array is stopped.  Moved packages to the snap.plg where they belong.  Updated to latest inotify package.  Fixed "No Fs" indicator when stopping a preclear and the disk has a valid file system.  Created ntfs-3g plugin to install ntfs-3g driver needed for writing to ntfs disks.
