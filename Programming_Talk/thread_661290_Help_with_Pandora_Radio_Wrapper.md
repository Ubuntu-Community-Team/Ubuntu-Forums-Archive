---
title: "Help with Pandora Radio Wrapper"
date: 2008-01-07
forum: Programming Talk
---

### Post by hollaburoo on 2008-01-07
I've been working on creating a very basic wrapper for Pandora Radio using Python and GTKMozembed.  I've gotten the player up and running but I've run into a snag getting multimedia keys to activate the builtin shortcuts for the player.  While the script recognizes when multimedia keys are pressed and sends a fake keypress to the mozembed widget, it doesn't do anything.

If anyone can figure out what's going wrong I'd be really grateful.  The script is attached.

This must be run before running script (it's a workaround to an Ubuntu bug)
```
export LD_LIBRARY_PATH=/usr/lib/firefox
export MOZILLA_FIVE_HOME=/usr/lib/firefox
```

---

### Post by feltre on 2008-01-20
Hi,

I'm not a python programmer, but I did some experiments... I set some handlers to the embed mozilla

```

        self.moz.connect('key-press-event', self.moz_key_press)
        self.moz.connect('key-release-event', self.moz_key_release)
        self.moz.connect('button-press-event', self.moz_button_press)

```

And neither of them were called when I used the pandora's interface. However, when one of your functions are called, for instance PlayPause, the handlers are called. 

So, the MozEmbed instance is the wrong widget to send the events; and I don't have any idea who should receive these events in order to perform the actions.

Please, post here the solution if you find it.

Cheers
Feltre

---

### Post by d41m40u on 2008-04-18
I know that Pandora now has keyboard shortcuts (as outlined [[COLOR="Blue"]here[/COLOR]]("http://blog.pandora.com/faq/#224").)  Is it possible for you to just use them somehow?  (Keep in mind that the player will have to retain focus, and I mean the flash player, not just the windows in which is resides.)

---

### Post by nulall on 2008-06-11
any progress with this project yet?

---

### Post by kerry_s on 2008-06-12
sounds interesting. i use the bookmarklet for pandora right now.

```

javascript:(window.open('http://www.pandora.com?cmd=mini','Pandora','width=728,height=380,menubar=no,toolbar=no,scrollbars=no,status=no,location=no,directories=no,resizable=false'))();

```

---

### Post by sq377 on 2008-06-12
How legal would it be to reverse the flash and create a true 3rd party client?  I would think that would be a much cleaner way (avoiding flash would be nice...).

---

### Post by nulall on 2008-06-12
similar to kerry_s's suggestion, i've been using the same address with prism for a nice compact app. the main problem is the lack of support for multimedia keys.

and i think a completely separate app that ran pandora independent of flash (or a plugin to let you run it in banshee or amarok) would be amazing. probably more legal than any of the stuff floating around that lets you download mp3s from pandora...

---

### Post by sq377 on 2008-06-12
I'm trying to find out definitely if a third party client is legal, and I'm guessing through the [DMCA that it is not]("http://www.chillingeffects.org/reverse/").  > On its face, since circumvention is generally required for reverse engineering, this prohibition would prevent reverse engineering of those measures that control access to a copyrighted work.

There is a clause allowing reverse engineering:
>  The exception allows reverse engineering of computer programs if the reverse engineer lawfully obtains the program, seeks permission from the copyright owner, only uses the results of their efforts to create an interoperable computer program and does not publish the results.
But I don't think this is covered.  Can anyone think of a way this could be legal?

---

### Post by AndThenWhat on 2009-12-23
> **sq377 said:**
> How legal would it be to reverse the flash and create a true 3rd party client?  I would think that would be a much cleaner way (avoiding flash would be nice...).

This has been done. It's a program called 'pianobar'.  I also have a completed Pandora Radio wrapper. It requires that you install pianobar first.  YouTube video to demonstrate:

[http://www.youtube.com/watch?v=Jc7FzQuZY9A](http://www.youtube.com/watch?v=Jc7FzQuZY9A)

---

### Post by nulall on 2009-12-24
> **AndThenWhat said:**
> This has been done. It's a program called 'pianobar'.  I also have a completed Pandora Radio wrapper. It requires that you install pianobar first.  YouTube video to demonstrate:

[http://www.youtube.com/watch?v=Jc7FzQuZY9A](http://www.youtube.com/watch?v=Jc7FzQuZY9A)

thanks for turning me on to pianobar! your wrapper looks great as well. i hope you continue to develop it further (it'd be nice to have an easy station selector)

---

### Post by jeepinpete on 2010-08-19
Check out pithos...

---

### Post by Dragonbite on 2010-08-19
> **sq377 said:**
> How legal would it be to reverse the flash and create a true 3rd party client?  I would think that would be a much cleaner way (avoiding flash would be nice...).

I was just about to suggest [[COLOR="Blue"]_Pithos_[/COLOR]]("http://kevinmehall.net/p/pithos/").

---

