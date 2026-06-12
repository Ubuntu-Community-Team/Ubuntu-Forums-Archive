---
title: "[SOLVED] f-spot photo manager"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by davarse on 2008-06-29
hi, in running hardy at the moment, i have a problem i cannot open f-spot photo manager. it just not open...
does anyone know what happened??

---

### Post by RomeReactor on 2008-06-30
Hi. Please open a terminal (Applications->Accessories->Terminal) and paste the following:
```
f-spot
```
Then press ENTER, and post any messages left in the terminal.

---

### Post by davarse on 2008-07-02
this the messeges that i got
[I]
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
[/I]

---

### Post by RomeReactor on 2008-07-02
Try moving your f-spot configuration out of its folder and into your home directory:
```
mv ~/.gnome2/f-spot ~
```
Then run f-spot again:
```
f-spot
```
If that doesn't help, try runing it like this:
```
dbus-launch f-spot
```

---

### Post by davarse on 2008-07-03
great it works
thanks heaps

---

### Post by merry_meerkat on 2008-09-05
Simply deleting the above mentioned directory did the trick for me (I had no photos in f-spot at the time).

Thanks!

---

### Post by s4n3j4v13r on 2009-12-16
can someone help me this is what i get when i run f-spot in the terminal.... thanks in advance


[Info  22:43:01.373] Initializing DBus
[Info  22:43:01.534] Initializing Mono.Addins
[Info  22:43:01.771] Starting new FSpot server (f-spot 0.6.1.5)

** (f-spot:6607): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:6607): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:6607): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:6607): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:6607): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
[Info  22:43:03.040] Starting BeagleService
[Info  22:43:03.066] Hack for gnome-settings-daemon engaged

(f-spot:6607): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
The program 'f-spot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 2031 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by s4n3j4v13r on 2009-12-16
can someone help me????

---

### Post by bwang on 2009-12-16
Try reinstalling F-Spot.
Also, posting in a thread that is marked SOLVED isn't the best way to get help.

---

### Post by alecwk on 2010-01-06
Had same problem. The problem was due to conflict between [COLOR=Red]F-Spot[/COLOR] and the "[COLOR=Red]New Wave[/COLOR]" Desktop Theme I was using. Changed the Desktop Theme to "[COLOR=Red]Dust[/COLOR]" and [COLOR=Red]F-Spot[/COLOR] launched with no problem.

---

### Post by adney on 2010-05-03
I'm using lucid and I've tried all of the fixes listed but f-spot still won't start, unless I run it as root.


[Info  12:48:17.080] Initializing DBus
[Info  12:48:17.205] Initializing Mono.Addins
[Info  12:48:17.403] Starting new FSpot server (f-spot 0.6.1.5)
[Info  12:48:17.484] Updating F-Spot Database

Unhandled Exception: Mono.Data.SqliteClient.SqliteSyntaxException: no such table: tags
  at Mono.Data.SqliteClient.SqliteCommand.GetNextStatement (IntPtr pzStart, System.IntPtr& pzTail, System.IntPtr& pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at Banshee.Database.QueuedSqliteCommand.Execute () [0x00000]

---

### Post by HC48 on 2010-05-10
hello, same here.

I have a similar problem in Lucid. I can't open f-spot  using the program menu but "sudo f-spot"  in the terminal opens it. It's strange because I used the same CD to  install Lucid as someone else who can open f-spot  in the normal way.
I have tried deleting and reinstalling with the graphic interface and  via the synaptic packets, restarting in between each action to no avail.  I can always use the terminal but would like to have the usual lazy way  if possible...
When I type f-spot in the terminal I get:
[Info  14:43:54.043] Initializing DBus
[Info  14:43:54.250] Initializing Mono.Addins
[Info  14:43:54.529] Starting new FSpot server (f-spot  0.6.1.5)
[Info  14:43:54.693] Updating F-Spot  Database

Unhandled Exception: Mono.Data.SqliteClient.SqliteSyntaxException: no  such table: tags
  at Mono.Data.SqliteClient.SqliteCommand.GetNextStatem  ent (IntPtr  pzStart, System.IntPtr& pzTail, System.IntPtr& pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior  behavior, Boolean want_results, System.Int32& rows_affected)  [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQue  ry () [0x00000]  
  at Banshee.Database.QueuedSqliteCommand.Execute () [0x00000] 

A similar problem here:
[http://ubuntuforums.org/showthread.php?t=1466070&highlight=F-spot](http://ubuntuforums.org/showthread.php?t=1466070&highlight=F-spot)

Any ideas?

Thank you,
H :)

---

