---
title: "Remote Banshee Command Line Inquiry"
date: 2011-07-29
forum: Programming Talk
---

### Post by jamesisin on 2011-07-29
Hi.  I wrote a small script for controlling Rhythmbox over the command line, especially for use across ssh (think remote control).  Since Ubuntu is moving toward Banshee I am working to create a similar script for it.  (The script should be much better as there are more controls available.)

Here is the Rhythmbox script:

[Script for Skipping Tracks]("http://jamesisin.com/a_high-tech_blech/index.php/2010/11/script-for-skipping-tracks/")

You will note that I make use of the $DISPLAY variable.  This is important in a remote situation so that the system knows where to locate the running instance of Rhythmbox.  (It is innocuous in a local situation.)

I have tried running the same basic command for Banshee but it spawns a new instance each time.  I have confirmed $DISPLAY on the remote box (using echo $DISPLAY.).

Here is my test command:

```
DISPLAY=:0.0 banshee --query-artist
```

This returns the artist when run locally (with or without DISPLAY).

Any ideas?

EDIT:

Ok. I threw together a script for review:

[http://jamesisin.com/a_high-tech_ble...ipping-tracks/](http://jamesisin.com/a_high-tech_ble...ipping-tracks/)

It is working well, but all feedback is appreciated.

---

### Post by jamesisin on 2011-07-30
Anyone else using Banshee?

---

### Post by jamesisin on 2011-07-30
My research indicates it is related to d-bus:

[http://machine-cycle.blogspot.com/2010/12/ssh-and-dbus-sessions.html](http://machine-cycle.blogspot.com/2010/12/ssh-and-dbus-sessions.html)

Here is another similar discussion:

[http://askubuntu.com/questions/53400/how-to-remotely-control-banshee-via-ssh](http://askubuntu.com/questions/53400/how-to-remotely-control-banshee-via-ssh)

---

### Post by MadCow108 on 2011-07-30
banshee exports an mpris interface over dbus:
[http://www.mpris.org/2.1/spec/](http://www.mpris.org/2.1/spec/)
with that you should be able to do almost everything.

to query some of the objects use e.g dbus-send or the higher level qdbus:

```

#display objects
qdbus org.bansheeproject.Banshee
qdbus org.mpris.MediaPlayer2.banshee /org/mpris/MediaPlayer2
#start play
qdbus org.mpris.MediaPlayer2.banshee /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Play

```

---

### Post by jamesisin on 2011-07-30
Maybe I'm not understanding what you are suggesting:

```
$ qdbus org.mpris.MediaPlayer2.banshee /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Play
Service 'org.mpris.MediaPlayer2.banshee' does not exist.
```

---

### Post by MadCow108 on 2011-07-30
dbus is pretty much the ideal interface to remote control banshee and by using the mpris interface your script will also be able to control any other complying player (I think rhythmbox and vlc also implement this interface)
banshee needs to be running in order to get this bus.

It also exports a few other buses which might provide features going beyond mpris
```

qdbus  | grep banshee
 org.bansheeproject.Banshee
 org.bansheeproject.CollectionIndexer
 org.mpris.MediaPlayer2.banshee

```

dbus-send should be available on more systems but is a bit more clunky, e.g. play next song:
```

dbus-send --session --type="method_call" --dest=org.mpris.MediaPlayer2.banshee /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Next

```

for more information on the very flexible dbus read:
[http://dbus.freedesktop.org/doc/dbus-tutorial.html](http://dbus.freedesktop.org/doc/dbus-tutorial.html)

---

### Post by SoFl W on 2011-07-30
"banshee command line" turned up [this thread]("http://ubuntuforums.org/showthread.php?t=1463211").

---

### Post by jamesisin on 2011-07-30
Thanks to both of you.

MadCow - The qdbus command only returns the first two entries on the machine in question.  Are there additional packages required for mpris?

SoFl W - I'll take a look.  I was hoping to write something in BASH and to keep it (as) portable (as possible), but this Python script may have some tricks I can use.

Thus far I have found that using this line makes my command usable:

```
export $(strings /proc/*/environ| grep DBUS_SESSION | tail -1)
```

If I run that first I am able to use the commands associated with banshee from the terminal (through ssh).

I suppose it would work to just add that line early in a script and all would be well.  I am not confident that is a wise maneuver since I am not familiar with what exactly is being exported.

---

### Post by jamesisin on 2011-08-01
Ok.  I threw together a script for review:

[http://jamesisin.com/a_high-tech_blech/index.php/2011/08/a-new-script-for-skipping-tracks/](http://jamesisin.com/a_high-tech_blech/index.php/2011/08/a-new-script-for-skipping-tracks/)

It throws a bunch of errors (I tried hiding using > /dev/null 2>&1 but it's not right), but it does what it's supposed to do.  If anyone can help me hide those errors it would be much appreciated.

---

### Post by jamesisin on 2011-08-02
I fixed a bunch of annoyances and slickified the script a bit.  It seems to be working quite well.

Any feedback is appreciated.

[http://jamesisin.com/a_high-tech_blech/index.php/2011/08/a-new-script-for-skipping-tracks/](http://jamesisin.com/a_high-tech_blech/index.php/2011/08/a-new-script-for-skipping-tracks/)

---

### Post by lautarop on 2011-08-03
Nice. Why did you have to make the play/pause, if it has the --toggle-playing option?


What i'd like to know too, if it is possible to have a seek script?

I want to bind two keys to seek trough the song
with the --set-position  option, I can only get to a specific second marc; is it possible to get something to do just a "+5" seconds ?

---

### Post by jamesisin on 2011-08-03
I don't believe there is a toggle option.  I just ran ```
man banshee | grep toggle
``` and it returned nothing.  That's why I built my own play/pause toggle.  If you have different information please share.

It would be possible to build seek functionality.

Also from the man page:

```
       --set-position=POS
              Seek to a specific point (seconds, float)

       --query-can-seek
              Query whether the player can seek

       --query-position
              Print player position in currently playing track

       --query-duration
              Print duration of current track
```

---

### Post by lautarop on 2011-08-03
Yeah, well maybe I'm confusing something, but if you do

[PHP]banshee --toggle-playing[/PHP]

it toggles betwenn pause and play


ps: I built banshee 2.10, and use ubuntu 11

---

### Post by jamesisin on 2011-08-03
Well, I stand corrected.  Sort of.

It's not listed in the man page, but --toggle-playing works in Banshee 1.6.1 as well.

So much for my clever solution...

---

### Post by jamesisin on 2011-08-05
I was hoping to work on the seek functionality but apparently there is a dependency bug which is preventing this functionality from working correctly:

[https://bugzilla.gnome.org/show_bug.cgi?id=541279](https://bugzilla.gnome.org/show_bug.cgi?id=541279)

---

### Post by lautarop on 2011-08-05
Yeah, that was a big pain in the ***, but actually it is solved if you're using ubuntu 11 and build banshe 2.10; dbus works perfectly.

I'd do it myself but I don't know how to code, maybe this is a good chance to learn how to do it

---

### Post by jamesisin on 2011-08-05
I see.  Would be nice to have this dbus fix tricked down into 10.04.

---

### Post by jamesisin on 2011-08-06
I added the code for seek functionality.  If anyone would like to test it that would be great (as I can't test it on my machine due to the dbus error mentioned above).

[http://jamesisin.com/a_high-tech_blech/index.php/2011/08/a-new-script-for-skipping-tracks/](http://jamesisin.com/a_high-tech_blech/index.php/2011/08/a-new-script-for-skipping-tracks/)

---

### Post by cefn on 2011-11-07
I had a whole lot of fun with making a PHP script which enables everyone in my office to control Banshee, Miro, Rhythmbox equally, based on XWindows media keys. Probably it will control video players and others.

This is based on the fact that, for example, ```
xdotool key XF86AudioPlay
``` will trigger playback. The additional keysyms for stop, pause, volume etc. are indicated below.

Note for this PHP page to work, assuming you're running it from a local apache2, you need to run...
```

xhost +local:

```
...to enable the xdotool invocations from your own machine (within the apache process) to be accepted by your X session.

[PHP]
<html>
<body>
<?php	

	$domap = array(	'prev' => "Previous",
			'stop' => "Stop",
			'play' => "Play",
			'pause' => "Pause",
			'next' => "Next",
			'mute' => "Mute",
			'louder' => "Increase Volume",
			'quieter' => "Lower Volume");

	$keymap = array('prev' => "XF86AudioPrev",
			'stop' => "XF86AudioStop",
			'play' => "XF86AudioPlay",
			'pause' => "XF86AudioPause",
			'next' => "XF86AudioNext",
			'mute' => "XF86AudioMute",
			'quieter' => "XF86AudioLowerVolume",
			'louder' => "XF86AudioRaiseVolume");

	$do = @$_GET['do']; 
	if($do){
		$keysym = @$keymap[$do];
		if($keysym){
			system("DISPLAY=:0.0 xdotool key " . $keysym);
		}
	}

?>
<div>
	<form action="index.php" method="GET" >
		<?php
			foreach($domap as $command=>$title){
				print("<input type='submit' name='do' value='$command'>$title </input>");
			}
		?>		
	</form>
</div>
</body>
<html>
[/PHP]

There may be a more secure way than adding local: to xhost in order to permit the keysym to be sent. If you find one, I would be happy to know it. I tried various setuid approaches with the xdotool in a self-contained, root-owned script but nothing I tried worked.

---

