---
title: "[SOLVED] f-spot doesn't start"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by pranayama on 2008-07-28
Hello. How do you handle applications that won't start? I clicked on F-spot for the first time, and a marker appeared in the bottom panel "Starting F-Spot Phot...", and then it vanished. I try again and the same thing happens, F-spot won't start.:confused:

---

### Post by pranayama on 2008-07-28
Terminal produces:

desktop:~$ f-spot
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

### Post by boilerbots on 2008-08-17
I had this problem and it wasn't that I needed to upgrade my database.

After trying several things the solution that worked for me was to first uninstall f-spot. Then completely delete what remained in the "/usr/lib/f-spot" directory. Then install the f-spot package again and it worked.

A quick experiment of putting back the extensions caused it to crash again, so it looks like it could be something in the extensions directory.

I am happing I can finally get my photos synced up again.

---

### Post by Raffles10 on 2008-08-17
When f-spot fails to start you may find it listed in your system monitor's processes list as "uninterruptible", if it is it will never start and trying to start it will only create more "uninterruptible" f-spot processes. You will have to reboot, it's the only way to stop "uninterruptible" processes.

I had the same problem with brasero & avidemux, complete removal and re-installation solved the problem both times:

sudo apt-get remove --purge f-spot
&
sudo apt-get install f-spot

should do it.

---

### Post by merry_meerkat on 2008-09-05
> **boilerbots said:**
> I had this problem and it wasn't that I needed to upgrade my database.

After trying several things the solution that worked for me was to first uninstall f-spot. Then completely delete what remained in the "/usr/lib/f-spot" directory. Then install the f-spot package again and it worked.

A quick experiment of putting back the extensions caused it to crash again, so it looks like it could be something in the extensions directory.

I am happing I can finally get my photos synced up again.

Uninstalling f-spot on my machine would also remove the directory you mention. Re-installing did nothing to solve the problem.

I did finally solve it by deleting a different directory: ~/.gnome2/f-spot

See here
[http://ubuntuforums.org/showthread.php?t=844823](http://ubuntuforums.org/showthread.php?t=844823)


Cheers.

---

### Post by pranayama on 2008-09-05
Thanks. Is there a name for these silly hidden preference files left behind after apt-get purge that block a proper reinstallation. They're annoying.

---

