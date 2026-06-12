---
title: "banshee won't start"
date: 2012-07-15
forum: New to Ubuntu
---

### Post by boweringguy on 2012-07-15
New to ubuntu just getting used to a lot of stuff. Don't really know why but recently I can't open banshee. I have 12.04 and I tried running it in terminal and this is what I got!


[Warn  09:43:04.555] DBus support could not be started. Disabling for this session. - System.ArgumentNullException: Argument cannot be null.
Parameter name: address (in `dbus-sharp')
  at DBus.Bus.Open (System.String address) [0x00000] in <filename unknown>:0 
  at DBus.Bus.get_Session () [0x00000] in <filename unknown>:0 
System.Exception: Unable to open the session message bus. (in `dbus-sharp')
  at DBus.Bus.get_Session () [0x00000] in <filename unknown>:0 
  at DBus.BusG.Init () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.DBusConnection.Connect (System.String serviceName, Boolean init) [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.DBusConnection.GrabDefaultName () [0x00000] in <filename unknown>:0 
[Info  09:43:04.762] Running Banshee 2.4.1: [Ubuntu 12.04 LTS (linux-gnu, i686) @ 2012-06-14 05:46:56 UTC]
[Info  09:43:07.347] Migrating album-art cache directory
[Warn  09:43:07.349] Caught an exception - Hyena.Data.Sqlite.SqliteException: Sqlite error 1: no such table: CoverArtDownloads (SQL: DELETE FROM CoverArtDownloads) (in `Hyena.Data.Sqlite')
  at Hyena.Data.Sqlite.Connection.CheckError (Int32 errorCode, System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.Connection.Execute (System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Hyena.Data.Sqlite.Connection connection) [0x00000] in <filename unknown>:0 
[Info  09:43:07.366] Migrated 0 files in 0.003303s
[Info  09:43:08.248] Updating web proxy from GConf
[Warn  09:43:16.132] Caught an exception - System.ArgumentNullException: Argument cannot be null.
Parameter name: address (in `dbus-sharp')
  at DBus.Bus.Open (System.String address) [0x00000] in <filename unknown>:0 
  at DBus.Bus.get_Session () [0x00000] in <filename unknown>:0 
[Warn  09:43:16.133] Extension `Banshee.SoundMenu.SoundMenuService' not started: Unable to open the session message bus.
[Warn  09:43:16.134] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  09:43:16.134] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.

(Banshee:23929): Gtk-WARNING **: Refusing to add non-unique action 'CloseAction' to action group 'Global'
[Warn  09:43:16.179] Caught an exception - System.ArgumentNullException: Argument cannot be null.
Parameter name: address (in `dbus-sharp')
  at DBus.Bus.Open (System.String address) [0x00000] in <filename unknown>:0 
  at DBus.Bus.get_Session () [0x00000] in <filename unknown>:0 
[Warn  09:43:16.179] Extension `Banshee.SoundMenu.SoundMenuService' not started: Unable to open the session message bus.
[Warn  09:43:16.179] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  09:43:16.179] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[Info  09:43:16.180] All services are started 9.44469
[Warn  09:43:16.452] Error migrating Internet Radio Stations - System.IO.DirectoryNotFoundException: Directory '/root/.config/banshee/plugins/stations/user' not found. (in `mscorlib')
  at System.IO.Directory.ValidateDirectoryListing (System.String path, System.String searchPattern, System.Boolean& stop) [0x00000] in <filename unknown>:0 
  at System.IO.Directory.GetFileSystemEntries (System.String path, System.String searchPattern, FileAttributes mask, FileAttributes attrs) [0x00000] in <filename unknown>:0 
  at System.IO.Directory.GetFiles (System.String path, System.String searchPattern) [0x00000] in <filename unknown>:0 
  at Banshee.InternetRadio.XspfMigrator.Migrate () [0x00000] in <filename unknown>:0 
[Info  09:43:16.521] AmazonMP3 store redirect URL: [https://one.ubuntu.com/music/store/amz/](https://one.ubuntu.com/music/store/amz/)
[Info  09:43:16.960] nereid Client Started
[Info  09:43:17.076] GStreamer version 0.10.36.0, gapless: True, replaygain: False
[Warn  09:53:44.214] Service disposal (MprisService) threw an exception - System.ArgumentNullException: Argument cannot be null.
Parameter name: address (in `dbus-sharp')
  at DBus.Bus.Open (System.String address) [0x00000] in <filename unknown>:0 
  at DBus.Bus.get_Session () [0x00000] in <filename unknown>:0 
System.Exception: Unable to open the session message bus. (in `dbus-sharp')
  at DBus.Bus.get_Session () [0x00000] in <filename unknown>:0 
  at Banshee.Mpris.MprisService.System.IDisposable.Dispose () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.Shutdown () [0x00000] in <filename unknown>:0 
[Warn  09:53:44.233] Unable to unregister DBus object Banshee.PlayQueue.PlayQueueSource, does not appear to be registered
Please help?

---

### Post by llamabr on 2012-07-15
Use those hash tags when you want to paste code, so it doesn't fill the whole screen.

Also, when you're pasting output, be sure to paste your input.  My guess is you tried to open banshee by using sudo.  Don't do that.

---

### Post by Shadius on 2012-07-15
Have you tried opening it up without using the Terminal?

---

### Post by digitography on 2012-11-30
I simply went to Software centre, removed banshee, then reinstalled. It remembered all my settings.

---

