---
title: "[SOLVED] VLC: Won't Save Prefs and Snapshots Won't Work"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by safetycopy on 2008-07-29
Hey,

I don't seem to be able to get VLC to save any of the preference changes I make, nor can I get it to take and save snapshots.

For example, I edit Preferences->Video->Video snapshot directory, then click save. When I go back to the same spot, the textbox is empty again.

When I click Alt+Ctrl+s to save a snapshot, nothing happens - the same when I select snapshot from the right-click menu or toolbar.

This is driving me bonkers :-) Anyone know what's going on?

---

### Post by caljohnsmith on 2008-07-29
As far as saving preferences in VLC, I've had the same problems, so I think it is simply a bug with VLC. You could try posting to their forums at forum.videolan.org and see if they can help you solve the bug.

---

### Post by safetycopy on 2008-07-30
Good idea - will give that a try and post back... Ta!

---

### Post by safetycopy on 2008-08-02
Bumping this because I'm still having the same problems and it's doing my head in! :-) The VLC forum seems to be dead as a doornail (which is pretty dead!), so anyone here have any thoughts?

---

### Post by caljohnsmith on 2008-08-02
I went and changed my Video snapshot directory in VLC, saved changes, restarted VLC, and the video snapshot directory was the new one I changed it to. So I'm not sure what your problem is, but what version are you using? I'm using the 0.8.6e version which is not even the latest.

Maybe it has something to do with how you are running VLC (I assume from the menus?). Try going to the command line and type "vlc", change your preferences, save, restart (at the CLI), and see if it saved your changes. Also look for any errors VLC outputs at the CLI--it may tell you it can't write the preferences you tried to save to your ~/.vlc directory for example. 

If that doesn't narrow down the problem, I would try uninstalling it, make sure your ~/.vlc directory is deleted (otherwise delete it manually), reinstall VLC, and see if that works.

---

### Post by safetycopy on 2008-08-02
I'm using VLC media player 0.8.6e Janus (wxWidgets interface)...

I'll give your suggestions a try - thanks!

---

### Post by safetycopy on 2008-08-02
Tried running from the CLI and changing my prefs as you suggested. When I hit Ctrl+C to stop vlc I get:

```
signal 2 received, terminating vlc - do it again in case it gets stuck
```

Then it just hangs. If I hit Ctrl+C again I get:

```
user insisted too much, dying badly
Aborted

```

I'll try reinstalling and getting rid of the ~/.vlc directory next...

---

### Post by caljohnsmith on 2008-08-02
Safetycopy, I just wanted to mention that you shouldn't have to use CTRL-C to quit VLC unless VLC locks up. Just exit VLC normally from the File > Exit menu selection. :)

---

### Post by safetycopy on 2008-08-03
OK - reinstall seems to have fixed things :-) Thanks!

Just a couple of questions:

You mentioned that I don't need to use Ctrl+C - I must confess I'm not really sure what this is for. I always use it to quit anything I start in a terminal. Am I doing something wrong?

Also, what's the difference between running a program from the CLI and running it by clicking menu launchers?

---

### Post by caljohnsmith on 2008-08-03
Ctrl-C is to interrupt a program you run in the command line and cause it to terminate immediately (in technical terms I think it sends the process a "SIGINT" signal). But many programs (mostly GUI) need to write to certain files and do certain "housekeeping" before they shut down to "cleanly" shut down, and not cause problems the next time you load them. So you should avoid using ctrl-C mostly with GUI programs you might run from the command line; but at the same time, Ctrl-C is a perfectly legitimate way of ending some simple commands that you might run at the command line. For instance, if I run a "find" command or a "ping" command, it certainly won't hurt to terminate them with a Ctrl-C.

And about running a command from the CLI or from the menus, there is absolutely no difference as long as you use the exact same command/arguments/options in both cases. But the advantage of running the program from the command line is that you get to see any error messages the program outputs.

---

### Post by safetycopy on 2008-08-04
Thanks for the reply - that's another useful note to store away. Posts like this are really helping me make the transition to Ubuntu!

---

