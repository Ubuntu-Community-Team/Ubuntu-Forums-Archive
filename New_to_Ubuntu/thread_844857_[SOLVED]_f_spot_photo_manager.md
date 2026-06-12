---
title: "[SOLVED] f spot photo manager"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by pdlethbridge on 2008-06-30
I tried to use f spot in hardy heron, but it would not open. Synaptic shows its loaded, but it fails to start. Could this be a bug?

---

### Post by Go_Bucks on 2008-06-30
Works on my system in Hardy. Have you tried reinstalling?

---

### Post by RomeReactor on 2008-06-30
Hi. Try running it from the terminal:
```
f-spot
```
and post any messages left there.

---

### Post by 7raTEYdCql on 2008-06-30
In the terminal put an ampersand after f-spot, cause that will block you from doing any other task from the terminal.

---

### Post by RomeReactor on 2008-06-30
> **i.mehrzad said:**
> In the terminal put an ampersand after f-spot, cause that will block you from doing any other task from the terminal.

Actually, uninterrupted output is what we want here, so we can try to pinpoint what the problem is. If there's need for the terminal afterwards, pressing CTRL+SHIFT+T gives you a new tab; but for now, what we need are the messages left there.

---

### Post by pdlethbridge on 2008-06-30
This what I got in terminal after a fresh install and upgrade of hardy.
(/usr/lib/f-spot/f-spot.exe:5784): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.16.3/gobject/gtype.c:2248: initialization assertion failed, use IA__g_type_init() prior to this function

(/usr/lib/f-spot/f-spot.exe:5784): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed

(/usr/lib/f-spot/f-spot.exe:5784): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
Stacktrace:

  at (wrapper managed-to-native) GConf.Client.gconf_client_get_default () <0x00004>
  at (wrapper managed-to-native) GConf.Client.gconf_client_get_default () <0xffffffff>
  at GConf.Client..ctor () <0x0003b>
  at FSpot.GConfPreferenceBackend.get_Client () <0x0001f>
  at FSpot.GConfPreferenceBackend.AddNotify (string,FSpot.NotifyChangedHandler) <0x00033>
  at FSpot.Preferences.get_Backend () <0x000ea>
  at FSpot.Preferences.Get (string) <0x00074>
  at FSpot.Driver.Main (string[]) <0x00144>
  at (wrapper runtime-invoke) FSpot.Driver.runtime_invoke_int_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	f-spot [0x816b1fa]
	f-spot [0x807de81]
	[0xb7f0f440]
	/usr/lib/libgconf-2.so.4(gconf_client_get_default+0xa9) [0xb6c029f9]
	[0xb7734de0]
	[0xb773487c]
	[0xb7734818]
	[0xb7734764]
	[0xb7734633]
	[0xb773417d]
	[0xb773093d]
	[0xb77301c4]
	f-spot(mono_runtime_exec_main+0x10e) [0x809c68e]
	f-spot(mono_runtime_run_main+0x173) [0x809c933]
	f-spot(mono_main+0x6a9) [0x805acd9]
	f-spot [0x805a122]
	/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7cc4450]
	f-spot [0x805a091]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7c6c940 (LWP 5784)]
[New Thread 0xb71e0b90 (LWP 5786)]
[New Thread 0xb7204b90 (LWP 5785)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xb7f0f410 in __kernel_vsyscall ()
  3 Thread 0xb7204b90 (LWP 5785)  0xb7f0f410 in __kernel_vsyscall ()
  2 Thread 0xb71e0b90 (LWP 5786)  0xb7f0f410 in __kernel_vsyscall ()
  1 Thread 0xb7c6c940 (LWP 5784)  0xb7f0f410 in __kernel_vsyscall ()

Thread 3 (Thread 0xb7204b90 (LWP 5785)):
#0  0xb7f0f410 in __kernel_vsyscall ()
#1  0xb7e2f196 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08105c91 in ?? ()
#3  0xb7e274fb in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7d84e5e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xb71e0b90 (LWP 5786)):
#0  0xb7f0f410 in __kernel_vsyscall ()
#1  0xb7e2baa5 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081088ff in ?? ()
#3  0x0810b3cd in ?? ()
#4  0x0810b43c in ?? ()
#5  0x0811ba1a in ?? ()
#6  0x080b1c0a in ?? ()
#7  0x080cef04 in ?? ()
#8  0x0811a7c2 in ?? ()
#9  0x081317a5 in ?? ()
#10 0xb7e274fb in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0xb7d84e5e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb7c6c940 (LWP 5784)):
#0  0xb7f0f410 in __kernel_vsyscall ()
#1  0xb7d7d881 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7eabe14 in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7eac1dc in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x0816b295 in ?? ()
#5  0x0807de81 in ?? ()
#6  <signal handler called>
#7  0xb6bff423 in ?? () from /usr/lib/libgconf-2.so.4
#8  0xb6c029f9 in gconf_client_get_default () from /usr/lib/libgconf-2.so.4
#9  0xb7734de0 in ?? ()
#10 0xb773487c in ?? ()
#11 0xb7734818 in ?? ()
#12 0xb7734764 in ?? ()
#13 0xb7734633 in ?? ()
#14 0xb773417d in ?? ()
#15 0xb773093d in ?? ()
#16 0xb77301c4 in ?? ()
#17 0x0809c68e in mono_runtime_exec_main ()
#18 0x0809c933 in mono_runtime_run_main ()
#19 0x0805acd9 in mono_main ()
#20 0x0805a122 in ?? ()
#21 0xb7cc4450 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#22 0x0805a091 in ?? ()
#0  0xb7f0f410 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

---

### Post by RomeReactor on 2008-06-30
Might be a problem with f-spot's configuration or its database; make a copy of the **~/gnome2/f-spot** folder in your home directory:
```
cp -R ~/.gnome2/f-spot ~
```
Then try running it like this:
```
dbus-launch f-spot
```

---

### Post by philinux on 2008-06-30
It's running fine for me, however there was this recent discussion on the 64-bit forum about f-spot not starting, and it's now solved.

[http://ubuntuforums.org/showthread.php?t=779044&highlight=f-spot](http://ubuntuforums.org/showthread.php?t=779044&highlight=f-spot)

---

### Post by pdlethbridge on 2008-06-30
this is what I got

WARNING: The add-in 'FSpot.__DefaultExporters,1.6' is trying to extend '/FSpot/Menus/Exports', but there isn't any compatible add-in defining this extension point
Unregistering [http://addins.f-spot.org/0.4.2/main.mrep](http://addins.f-spot.org/0.4.2/main.mrep)
Starting new FSpot server
XXXXX
Mono.Data.SqliteClient.SqliteSyntaxException: no such table: tags
  at Mono.Data.SqliteClient.SqliteCommand.GetNextStatement (IntPtr pzStart, System.IntPtr& pzTail, System.IntPtr& pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader () [0x00000] 
  at (wrapper remoting-invoke-with-check) Mono.Data.SqliteClient.SqliteCommand:ExecuteReader ()
  at Banshee.Database.QueuedSqliteCommand.Execute () [0x00000] 
XXXXX
Can't get a connection to the dbus. Trying again...
Starting new FSpot server
Can't get a connection to the dbus. Trying again...
Starting new FSpot server
Can't get a connection to the dbus. Trying again...
Starting new FSpot server
Can't get a connection to the dbus. Trying again...
Starting new FSpot server
Can't get a connection to the dbus. Trying again...
Starting new FSpot server
Can't get a connection to the dbus. Trying again...
Sorry, couldn't start F-Spot

---

### Post by pdlethbridge on 2008-06-30
I found the problem. Apparently I'm having issues with the home folder. It has happened before and the only way I get solve the issues was to dump all ubuntu settings in the home folder. Of course, I've saved all the important stuff. so the problem is solved

---

### Post by gitpik on 2008-06-30
EDIT:found it sorry for the extra bump :(

Hi! I see this thread is already marked as solved but I was wondering if you could direct me to what files you cleaned out to get f-spot running again. It hasn't worked for me for some time. Here is my terminal output.

$ f-spot
Starting new FSpot server
XXXXX
Mono.Data.SqliteClient.SqliteSyntaxException: no such table: tags
  at Mono.Data.SqliteClient.SqliteCommand.GetNextStatement (IntPtr pzStart, System.IntPtr& pzTail, System.IntPtr& pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader () [0x00000] 
  at (wrapper remoting-invoke-with-check) Mono.Data.SqliteClient.SqliteCommand:ExecuteReader ()
  at Banshee.Database.QueuedSqliteCommand.Execute () [0x00000] 
XXXXX
Can't get a connection to the dbus. Trying again...
Starting new FSpot server
Can't get a connection to the dbus. Trying again...
Starting new FSpot server
Can't get a connection to the dbus. Trying again...
Starting new FSpot server
Can't get a connection to the dbus. Trying again...
Starting new FSpot server
Can't get a connection to the dbus. Trying again...
Starting new FSpot server
Can't get a connection to the dbus. Trying again...
Sorry, couldn't start F-Spot

---

### Post by RomeReactor on 2008-06-30
Try moving your **~/.gnome2/f-spot** folder out of **~/.gnome2**:
```
mv ~/.gnome2/f-spot ~
```
And try to open f-spot again:
```
f-spot
```
Or:
```
dbus-launch f-spot
```

---

