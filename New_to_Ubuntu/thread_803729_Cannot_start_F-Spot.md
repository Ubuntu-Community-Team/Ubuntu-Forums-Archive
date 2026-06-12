---
title: "Cannot start F-Spot"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by Oliwer Emerich on 2008-05-22
I'm tried to run the F-Spot but it doesn't want to work ... after a while the icon from the pannel disappears and nothing happens. I think I was opening this program before without any problems ...

When I try to start it from the terminal it writes:

Can't get a connection to the dbus. Trying again...
Sorry, couldn't start F-Spot


Anyone can help?

I'm new to linux, so please take it easy with your answers ;-)****

---

### Post by philinux on 2008-05-22
You need to read all this thread if your running 64 bit or not.

[http://ubuntuforums.org/showthread.php?t=779044](http://ubuntuforums.org/showthread.php?t=779044)

---

### Post by Oliwer Emerich on 2008-05-22
solved - thanks a lot!

---

### Post by izirider on 2010-07-10
hello everybody! got a problem: cannot start f-spot. a day before yesterday saved my phtos in a new directory. at the beginning marked a "always perform this action" in "import photos" window. now trying to launch it - doesn't works. starting in terminal appears:

miha@tormentor:~$ dbus-launch f-spot
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
miha@tormentor:~$ 


reinstalling didn't worked too, as a complete removing and installing over again. any ideas? thank you!

---

### Post by lidex on 2010-07-11
Completely remove it again. Now do these commands in a terminal:
```
sudo updatedb
sudo locate f-spot
```
That will show you where any remaining config files are. Delete them.
Now this:
```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install f-spot
```

---

### Post by azertyh on 2010-07-11
hi,
delete the folder ~/.config/f-spot.

---

### Post by izirider on 2010-07-11
> **lidex said:**
> Completely remove it again. Now do these commands in a terminal:
```
sudo updatedb
sudo locate f-spot
```
That will show you where any remaining config files are. Delete them.
Now this:
```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install f-spot
```

hi! tried as you said - "the song remains the same"... :confused:

---

### Post by lidex on 2010-07-11
I got it working that way, then I deleted it, because I don't use it. YMMV. Guess you could try downgrading.

---

