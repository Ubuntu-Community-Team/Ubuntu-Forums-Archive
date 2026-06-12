---
title: "Run: ProtocolHandler"
date: 2007-05-07
forum: Programming Talk
---

### Post by RawMustard on 2007-05-07
There's a little program we use at work called [Run: ProtocolHandler 2.0]("http://www.blackbit.net/frames/software.html")
We use it to launch all kinds of stuff from Firefox on our local Intranet.  It's become so useful, most of the guys never ever see their desktops, just Firefox :)

Anyway, I was thinking this could possibly be done using a bash script under Linux.  Firefox already has the ability to set up new protocol handlers, so it would just be a matter of sending a link from Firefox to a bash script and having the script intercept the link and perform a function i.e. execute something.

I've hunted the web high and low to try and find a way to capture external data in a script, but unfortunately, I'm not a programmer so I probably didn't see what I was looking for anyway even though it was right infront of me :)

Anyone here might have a clue how I could go about writing something like this up.  Or give me a hint how I can capture a link in Firefox to a script and have that script print out to screen what the link was, that would be enough to get me on my way :)

---

### Post by kidders on 2007-05-08
Hi there,

I'd never tried to do this before, but I thought I'd play around and see what happens. The following (most of which you probably already know) seemed to work for me...

```
$ firefox --version
Mozilla Firefox 2.0.0.3, Copyright (c) 1998 - 2007 mozilla.org
```

```
$ grep silly ~/.mozilla/firefox/[random].default/prefs.js 
user_pref("network.protocol-handler.app.silly", "~/firefox-test");
user_pref("network.protocol-handler.external.silly", true);
```

```
$ grep expose-all /usr/share/firefox/defaults/pref/firefox.js
pref("network.protocol-handler.expose-all", true);
```

```
$ cat ~/firefox-test 
#!/bin/bash
echo $@ >>/tmp/firefox.crap
```

Opening Firefox, and visiting **silly://whatever** produces...
```
$ cat /tmp/firefox.crap
silly://whatever
```

I noticed a few things, however...
[LIST]
[*]Firefox seems to be a little inaccurate with its error messages. Deleting or **chmod -x**-ing my protocol handler script made my firefox tell me my test protocol (silly://) "isn't associated with any program" ... which is unhelpful.
[*]Quoting the name of my handler script (which I figured would be good practice, even if not strictly necessary in my example) broke it ... so handling paths with special characters in them could prove awkward.
[*]I tried breaking my handler by visiting "silly://whatever>/tmp/something", just to see what would happen. Thankfully, Firefox's parameter escaping seems to work.
[/LIST]

Is that any help?

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by RawMustard on 2007-05-08
Wow!  Thanks, I didn't expect that much :)

Anyway, I haven't tried it yet but I'll report back here my own findings in a day or two.  This could be a useful little script in linux I think, it sure is in windows.

Again, thanks for your input :)

---

### Post by kidders on 2007-05-08
> **RawMustard said:**
> Wow!  Thanks, I didn't expect that much :)Hehe no problem.

> **RawMustard said:**
> This could be a useful little script in linux I think, it sure is in windows.Making a useful script would require a little work. I would suggest something like this...
[LIST]
[*]You could create a single master script (eg /usr/local/bin/protocol-delegator) that you would use for _all_ custom protocol handlers in Mozilla software.
[*]The master script would be responsible for identifying the protocol and launching the correct application (or perhaps doing more elabourate things). This might be useful... ```
$ echo "http://www.google.ie/" | cut -d":" -f1
http
```... Tools like **cut** let you extract the name of the requested protocol from the master script's command line arguments. You could then follow up with a long list of "if" statements.
[*]If you wanted, you could get more elaborate, and use the PID of the master script's parent process to distinguish between invocations out of Firefox, and invocations out of Thunderbird ... so they could each behave differently.
[/LIST]

One observation I would make is that Linux users (security-conscious as they are) often don't like blurring the line between the big bad world and their own PC. Essentially, protocol handlers like these are convenient, but "feel" dangerous. Related to that issue, I would strongly suggest that this be the first line of any protocol handling script...

```
if [ "`whoami`" = "root" ]; then echo "No way in hell, mister."; exit 1; fi
```

Looking forward to hearing how it goes!

---

### Post by RawMustard on 2007-05-10
Hi, I've had a bit of time to play with all that you suggested, and it's going to work ok once I can get all my bash scripting abilities up to somewhere near beginner :)

Thanks for the "cut" tip, that's a good one, I can see myself using that a lot in the future :)

To stop firefox giving the error you mentioned, it was just a matter of adding:
```
user_pref("network.protocol-handler.warn-external.silly", false);
```

Now my problem is assigning this filter command to a variable, $truePath.
```
truePath=$@ | cut -d'#' -f3 | sed 's_\\_/_g' | sed 's_//servername/_/media/SN-_'
```  My variable seems to contain nothing no matter how I write it, I've read about backticks and all sorts of stuff, nothing seems to work I must be missing something:(

$@ conatains:
```
run:{open}#tsmsec#\\servername\Movies1\Action\2 Fast 2 Furious.mkv
``` before running it through the filter command (is that the right term?)

My filters are working correctly, but soon as I try to assign the output to a variable I get no output from echo $truePath.  I was hoping you might be able to help me out a bit with this.

Oh and for security, I'm searching for the #tsmsec# before running the script, so if it doesn't find it, the script just exits.  Also in my case, the script will only be allowed to run harmless files such as .odt, video and music files.  Anything else will abort the script.

OK I got it:```
truepath=$(echo $@ | cut -d'#' -f3 | sed 's_\\_/_g' | sed 's_//servername/_/media/SN-_')
``` Which outputs:```
/media/SN-Movies1/Action/2 Fast 2 Furious.mkv
```

Now to tell it what app to use.  I wonder if there's a way to tell it to use the default app associated with .mkv files?

---

### Post by kidders on 2007-05-10
Hey again,

> **RawMustard said:**
> To stop firefox giving the error you mentioned, it was just a matter of adding:
```
user_pref("network.protocol-handler.warn-external.silly", false);
```Thanks for the tip. :-)

> **RawMustard said:**
> I was hoping you might be able to help me out a bit with this.I'd be happy to try. It looks as though you're trying to map what is effectively a Microsoft networking share path to a Linux mount point, although I'm not 100% sure.

[LIST]
[*]My first step would be to do a **sed 's_\\_/_g'**, as you've done.
[*]Then I would search the output of **mount** for anything that matched the start of the result. You would be looking for "//servername/Movies1", or maybe even "//servername/Movies1/Action" ... either would give you a means of accessing the requested file.
[*]If there is no suitable mount point, I would maybe use **smbtree** to try to identify the right server & share, and then mount it somewhere.
[/LIST]

That way, your script would tolerate unexpected /media directory names, and could handle network paths that existed, but you had forgotten to mount.

> **RawMustard said:**
> ```
truePath=$@ | cut -d'#' -f3 | sed 's_\\_/_g' | sed 's_//servername/_/media/SN-_'
```Eek... be a little careful there! Try inserting the word **echo** between '=' and '$' (ie **truepath=echo "$@" | cut ...**). It's occasions like this where you have to think about security issues, since it could be possible, for example, to construct a server name that would cause arbitrary code execution here.

I hope that helps.

---

### Post by RawMustard on 2007-05-10
Yeah, the shares are on a win2k server and we already have several win users accessing the shares via the app I'm trying to replicate. So for this, I have to translate everything to Linux talk :(  It would be so much easier if it were all Linux :)

>     * Then I would search the output of mount for anything that matched the start of the result. You would be looking for "//servername/Movies1", or maybe even "//servername/Movies1/Action" ... either would give you a means of accessing the requested file.
    * If there is no suitable mount point, I would maybe use smbtree to try to identify the right server & share, and then mount it somewhere.


That way, your script would tolerate unexpected /media directory names, and could handle network paths that existed, but you had forgotten to mount.

That's a great Idea, I never thought of that.  But as this is for my own machine at work and my shares are setup in fstab, I know what they are.  Perhaps I'll add this later :)

> Eek... be a little careful there! Try inserting the word echo between '=' and '$' (ie truepath=echo "$@" | cut ...). It's occasions like this where you have to think about security issues, since it could be possible, for example, to construct a server name that would cause arbitrary code execution here.


But if the very first line of my script determines if the security word is present before running the script wouldn't that be enough?

---

### Post by kidders on 2007-05-10
> **RawMustard said:**
> But if the very first line of my script determines if the security word is present before running the script wouldn't that be enough?I guess so. It's purely a question of what you're happy with. :-)
Did my "echo" suggestion make a difference?

---

### Post by RawMustard on 2007-05-10
I did it this way:```
truepath=$(echo $@ | cut -d'#' -f3 | sed 's_\\_/_g' | sed 's_//servername/_/media/SN-_')
```
Is that better?

Now that I have my path and app correct in a variable $filelnch which contains:```
totem "/media/SN-Movies1/Action/2 Fast 2 Furious.mkv"
```
totem launches but does not open the file, I get error location not found.  If I type that command into a terminal, it works fine and if I pipe it to firefox.crap I get the full string written.

Is there a command I have to type before $filelnch to make it pass the whole string to totem?

Sorry if this is a dumb question, but this is the most complex bash script I've ever written, so I'm learning as I go. It's hard breaking the old windows habits :)

Oh and thanks for your input, I've learned heaps just doing this little project, linux is so much fun :)

---

### Post by RawMustard on 2007-05-10
Or is there a way I can see what's actually being passed to totem?

---

### Post by RawMustard on 2007-05-10
Hmm - So it's appending "/home/usrname/" to my path, so I get this being sent to totem:
```
"/home/usrname/"/media/SN-Movies1/Action/2"
```

Any tips on how to stop it appending "/home/usrname/"

Arg! - I just noticed it's cutting off half the file name also :(

---

### Post by kidders on 2007-05-10
Lol there seem to be lots of things going funny, all at the same time!

When scripting in Linux, you need to pay close attention to special characters ... I'm guessing that's the source of your problems. There are lots and lots of subtle (but vitally important) distinctions, that ... well ... to be honest, it's all a bit of a nightmare!

An example:
```
$ echo "Hello!"
-bash: !": event not found
```
```
$ echo Hello!
Hello!
```

Another one:
```
$ echo "\\"
\
$ echo '\\'
\\
$ echo \\
\
```

Confused yet?

Some other examples of characters you should **never** use without taking precautions are **~*[]();** ... one of those ('~') is the only place I can think of that your home directory path could be coming from:

```
$ echo ~
/home/kidders
$ echo "~"
~
```

Unescaped characters (especially spaces!) can have odd effects if not handled correctly. (This is chiefly what I was referring to when I mentioned the potential for security issues earlier.) In practical terms, "/media/SN-Movies1/Action/2" probably appears trucated because the variable holding the full path wasn't quoted. It would be the difference between **sudo rm -Rf / strange** and **sudo rm -Rf "/ strange"**. One would erase your entire filesystem; the other would remove a file called " strange" (ie with a space at the start of the name) that lives in your root directory.

As if this wasn't complicated enough, Bash often silently unescapes things once it's stored them in a variable, for instance. So, once you start accepting input from users (ie via Firefox), you have to start entertaining all sorts of odd things ... including *malicious* things. Scripters quite often end up with commands comprising long, convoluted sequences of nested backticks, brackets and single & double quotes, just to perform basic manipulations. Another way of looking at it though, is that the ability to make such subtle distinctions exposes tremendous power, that is not present in all scripting languages.

So, just off the top of my head, I would personally prefer to write ...

```
truepath=$(echo $@ | cut -d'#' -f3 | sed 's_\\_/_g' | sed 's_//servername/_/media/SN-_')
```

... like this ...

```
truepath="$(echo "$@" | cut -d'#' -f3 | sed 's_\\_/_g' | sed 's_//servername/_/media/SN-_')"
```

Sorry for rabbiting on for so long! The short answer to your question is "Over time, you will develop an instinct for when to use (or *not* to use) things like backticks, single & double quotes, to control how variables are interpreted."

> I've learned heaps just doing this little project, linux is so much funHehe... messing around with scripts can be entertaining. :-P

---

### Post by RawMustard on 2007-05-13
Hey Kidders, thanks for all your input, you were a great help! :)

Here's where I'm at, at the moment.
```

#!/bin/bash
# FirefoxRun - 0.01

#########################################################################
#                                                                       #
# This program is free software; you can redistribute it and/or modify  #
# it under the terms of the GNU General Public License as published by  #
# the Free Software Foundation; either version 2 of the License, or     #
# (at your option) any later version.                                   #
#                                                                       #
#########################################################################

#Takes input from a specially formatted link in a webpage and allows Firefox to launch media files in your selected media player.

# You must add these lines (Excluding the # symbol) to your user created user.js file in your Firefox profile directory.
#
# user_pref("network.protocol-handler.app.run", "~/scripts/FirefoxRun");
# user_pref("network.protocol-handler.external.run", true);
# user_pref("network.protocol-handler.warn-external.run", false);
#
# You can set ~/scripts to any directory you like. Make sure it matches the entry in your user.js file though :)

# Format your links like so in your webpage.
#
# <a href="run:{open}#SecretWord#\\ServerName\DirectoryName\MediaFile.ext">Filename or link name</a>
# The SecretWord can be any word you like eg. ABCE, NOWAY, buggeroff. Just make sure it matches the one you set in this script.

  SecretWord="SecretWord" # Our SecretWord
  videoApp="totem"    # Not fully utilised yet.
  musicApp="totem"    # Not fully utilised yet.

securityWord="$(echo $@ | cut -d'#' -f2)" # Extracts our secret word from our link.
if [ "$securityWord" = "$SecretWord" ]    # Checks if the secret word is correct.
   then
        truePath="$(echo $@ | cut -d'#' -f3 | sed 's_\\_/_g' | sed 's_//ServerName/_/media/SN-_g')" # Converts Windows path to Unix path.
        filePath="$(echo ${truePath%/*})"  # Gives us the path to the file.
        fileName="$(echo ${truePath##*/})" # Gives us the File Name.
        cd $filePath # Moves us into the correct directory where the file lives.
else
        zenity --error --text="Incorrect Security Word\!"; exit 1; # Displays a dialog window telling us we have the wrong secret word.
fi

file -b "$fileName" | grep "Matroska\|OGM\|Ogg\|AVI\|QuickTime\|MPEG\|MP3\|ASF\|FLAC"  # Only allows certain file types by their mime types.
if [ $? -eq 0 ]
   then
      $videoApp "$fileName"
else
      zenity --error --text="Disallowed file type\!"; exit 1; # Displays a dialog telling us the file type is not allowed.
fi
exit 0
```

It works fantastically :)

I still want to add to it to make it better, check if the directory or file exists, have a different player for different media types and improve the security bit a bit more if I can.  This one is for a win server at work but I'm setting this up at home to work off my Linux server and creating a media portal using php that lets me see all my movies, music in firefox and launch them.  Using php and html, makes it easy to build your own media centre without complex programming knowledge :)

This was my first real attempt at bash scripting so excuse me if things could have been done more efficiently.  Anyway, your input was most welcomed, thankyou :)

---

### Post by kidders on 2007-05-13
Nice work! :-) Glad I could help.

---

