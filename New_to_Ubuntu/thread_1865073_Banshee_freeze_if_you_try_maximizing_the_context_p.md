---
title: "Banshee freeze if you try maximizing the context pane"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by dentar on 2011-10-19
Hello guys,

I just upgraded to 11.10 OO and I started to face problem with banshee.

If I click on small square which say "Make the context pane larger or smaller" then banshee freeze.

Anyone experienced this behavior?

Many thanks, J.

---

### Post by Ken J. Brown on 2011-11-17
Yes, This is happening to me too.. I have to kill Banshee cause it goes dark. I added the Lyrics Extension and would like to see more of the Lyrics when a song is playing. I click on the little box and Banshee freezes up. 

Does anyone have a fix for this?

---

### Post by MG&amp;TL on 2011-11-17
Please open a terminal and run:

```
banshee
```

and provide the output. Do whatever you did to get it to crash.

---

### Post by Ken J. Brown on 2011-11-17
Here's the output. The song will finish but banshee will not continue to the next song. My CPUs go to about 80% during this. I have to stop it with the X and force quit.

```
ken@ken-LifeBook-V1020:~$ banshee
[Info  09:23:42.206] Running Banshee 2.2.0: [Ubuntu oneiric (development branch) (linux-gnu, i686) @ 2011-09-23 04:51:00 UTC]
[Info  09:23:44.086] Updating web proxy from GConf
[Info  09:23:44.564] All services are started 1.937539
[Info  09:23:49.427] AmazonMP3 store redirect URL: https://one.ubuntu.com/music/store/amz/
** (Banshee:2687): DEBUG: SyncDaemon already running, initializing SyncdaemonDaemon object

(Banshee:2687): libsoup-WARNING **: No feature manager for feature of type 'U1RequestChrome'
[Info  09:23:51.797] nereid Client Started
[Info  09:23:52.102] GStreamer version 0.10.35.0, gapless: True, replaygain: False
[Warn  09:23:52.496] Caught an exception - System.ArgumentNullException: Argument cannot be null. (in `mscorlib')
  at System.Int32.Parse (System.String s, NumberStyles style, IFormatProvider provider) [0x00000] in <filename unknown>:0 
  at System.Int32.Parse (System.String s, NumberStyles style) [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.Gio.UsbDevice.GetVendorId (IUsbDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.Gio.UsbDevice.get_VendorId () [0x00000] in <filename unknown>:0 
  at Banshee.Dap.MassStorage.DeviceMapper.Map (Banshee.Dap.MassStorage.MassStorageSource source) [0x00000] in <filename unknown>:0 
  at Banshee.Dap.MassStorage.MassStorageSource.DeviceInitialize (IDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] in <filename unknown>:0 

** (Banshee:2687): WARNING **: Error calling get_info: Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/platform/linux/dbus_interface.py", line 1041, in get_info
    return self.syncdaemon_folders.get_info(path)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 640, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/syncdaemon/filesystem_manager.py", line 781, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/ken/.ubuntuone/Purchased from Ubuntu One'


** (Banshee:2687): CRITICAL **: syncdaemon_folder_info_get_subscribed: assertion `SYNCDAEMON_IS_FOLDER_INFO (finfo)' failed

** (Banshee:2687): WARNING **: Error rescanning Purchased Music: No such file or directory
** (Banshee:2687): DEBUG: Loading the real store page
[Info  09:24:13.449] Uncached artwork size 230 requested
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.ArgumentException: Value does not fall within the expected range.
  at Hyena.Gui.Canvas.Rect.set_Height (Double value) [0x00000] in <filename unknown>:0 
  at Hyena.Gui.Canvas.Rect.op_Explicit (Rectangle rect) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Gui.ListView`1[Banshee.Collection.AlbumInfo].OnSizeAllocated (Rectangle allocation) [0x00000] in <filename unknown>:0 
  at Gtk.Widget.sizeallocated_cb (IntPtr widget, IntPtr allocation) [0x00000] in <filename unknown>:0 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Widget.sizeallocated_cb(IntPtr widget, IntPtr allocation)
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Banshee.Gui.GtkBaseClient.Run()
   at Banshee.Gui.GtkBaseClient.Startup()
   at Hyena.Gui.CleanRoomStartup.Startup(Hyena.Gui.StartupInvocationHandler startup)
   at Banshee.Gui.GtkBaseClient.Startup()
   at Banshee.Gui.GtkBaseClient.Startup(System.String[] args)
   at Nereid.Client.Main(System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.AppDomain , System.Reflection.Assembly , System.String[] )
   at System.AppDomain.ExecuteAssemblyInternal(System.Reflection.Assembly a, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile)
   at Booter.Booter.BootClient(System.String clientName)
   at Booter.Booter.Main()
Killed
ken@ken-LifeBook-V1020:~$ 

```

Thanx for your help!

---

### Post by MG&amp;TL on 2011-11-17
No problem, short of 'don't maximise the context pane' - I can't give much direct help. The program has encountered a severe error that only a developer of banshee would know what to do with.

However, if you would like to contribute to banshee(and please do!) could you file a bug as described here: [http://banshee.fm/contribute/file-bugs/]("http://banshee.fm/contribute/file-bugs/") and with a bit of luck they will fix it. You will then have contributed to the open-source movement and made your mark on things. :D Normally, however, projects in ubuntu are bug-tracked here:  [http://launchpad.net]("http://launchpad.net").

Incidentally, if you are just after a media player, you can use rhythmbox (which will be installed in 12.04). You can install it in software-centre.

Sorry I can't be of more help, and please do file the bug.

---

