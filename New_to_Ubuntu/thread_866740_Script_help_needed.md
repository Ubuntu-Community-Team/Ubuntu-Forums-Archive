---
title: "Script help needed"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by MaxVK on 2008-07-22
Hi there, I'm in need of some help with a script, assuming what I want to do can actually be done!

I suffer from RSI (Only a little bit of numbness at the moment, but I'm playing safe) and as a result I have a mouse and a trackball that I can use, as well as swapping the trackball to my left hand.

I can configure all of this in xorg.conf, but Id like to have a script that I can run by clicking an icon on the desktop, that will swap the xorg.conf files for each device.

So for example, I click Icon#1 and it swaps the xorg.conf to the one with the left handed trackball configuration, and then logs out so I can log back in with the correct device. Id need three scripts, each swapping to a different xorg.conf and a different device.

Can this be done, and if so could anyone help me with an example that I could work from. Please remember that I'm pretty new to Linux and I have not delved into scripting at all just yet.

Many thanks

Max

---

### Post by Vadi on 2008-07-22
Can't help on the script, but if you don't have this yet, [install workrave]("apt:workrave"). Then right-click on the panel, 'Add to Panel', search for workrave and add it. It's a very handy thing to help against / in case of RSI :)

---

### Post by Potatoj316 on 2008-07-22
you could save 3 versions of the file you want to change, one with the original name, one with name_right, and one with name_left.  Then write a script that copies (cp) either right or left to the actual config file.

---

### Post by hyper_ch on 2008-07-22
but exchanging xorg.conf won't alter the behaviour in the current session - at least that's what I think... you'd rather need to have script that issue the commands instead.

---

### Post by MaxVK on 2008-07-22
I'm not expecting the replacement xorg.conf to have an effect straight away, which is why I think that the script(s) should log me out (Like CTRL-Backspace). Again, I don't know if this can be done from a script, but in any case I can live with pressing those two buttons myself if I have to.

Vadi - Workrave
Ill look into this as soon as Im on my own machine again.

Thanks for your replies. If anyone has any code they could explain Id certainly appreciate it, for example, HOW would I create a script that I can click on, and how would I get it to copy the config files for me?

Thanks everyone

Max

---

### Post by Lord DarkPat on 2008-07-22
it won't matter if you make different xorg.conf's
you will need to implement the functions in the existing one
and, I don't think this'll be easy....I'll just mess around with my xorg and see what I can do

---

### Post by ConMan318 on 2008-07-22
Well as far as a script that does what you want, that's simple.  Whether what you want to do will work or not is the question.  Here's a script for you:
```

#!/usr/bin/perl

`cp **~/.xorg.conf.layoutOne** /etc/X11/xorg.conf`;
`/usr/bin/gnome-session-save --kill --silent`;

```

The bold text is a hidden file in your home folder (you'll have to make this) that gets copied to your xorg.conf file.

What you would need to do is save this on your desktop, so open up a terminal and type:
```

cd ~/Desktop
touch **switchToLayoutOne**
gedit **switchToLayoutOne**

```

and paste in that code above.  If you type it rather than paste it, notice that the characters surrounding the commands are back-ticks, not apostrophes.  Obviously you can name this file whatever you want, I just bolded it to show it had to match with the below.  Then you are going to have to make it executable (this is how you can run it by double-clicking), so go ahead and type this in the terminal:
```

chmod 755 **switchToLayoutOne**

```

So now all you need to create is that hidden file in your home directory that holds the new xorg.conf that is replacing the old one.

Since you said you could configure that, after it's configured, move that file to the bolded filename in the program I posted.  If you have been configuring that alternate file in 'Documents', do:
```

mv ~/Documents/yourBackupFileName.conf ~/.xorg.conf.layoutOne

```

Note that you can put this file anywhere you want, but if you move it somewhere else, you must update the program file with the correct path/filename.  The text that I bolded in the actual program at the beginning of this post must match your file locations/names.



So now you have one executable sitting on your desktop that switches your xorg.conf file to the one saved in a hidden file in your home directory.  You wanted three, so do this:
```

cp ~/Desktop/switchToLayoutOne ~/Desktop/switchToLayoutTwo
cp ~/Desktop/switchToLayoutOne ~/Desktop/switchToLayoutThree

```

Now you have three differently named files on your desktop, but they are all the same program.  So update the code in the two new ones to swap xorg.conf with different files.  Like this:
```

gedit ~/Desktop/switchToLayoutTwo

```

Then change the line that says
```

`cp ~/.xorg.conf.layoutOne /etc/X11/xorg.conf`;

```

to
```

`cp ~/.xorg.conf.layoutTwo /etc/X11/xorg.conf`;

```




Do the same update with "switchToLayoutThree", obviously in that one change the filename from "~/.xorg.conf.layoutOne" to "~/.xorg.conf.layoutThree".

Now you have all your executables.  All that's left is making the two other alternate xorg.conf files.  Place them in "~/.xorg.conf.layoutTwo" and "~/xorg.conf.layoutThree".  Then all you have to do is double-click a file to swap your xorg.conf and logout.

If you are wondering about the period in front of these files I told you to make, they are so the files appear hidden.  That means they won't show up in your file browser (unless you press Ctrl + H) and they won't show up in an 'ls' command (unless you use 'ls -a').  This just makes it less likely you will accidentally modify them, and it won't look like your home directory is cluttered.

Hopefully you can get the alternate xorg.conf files to make this work.

Good luck!

---

### Post by MaxVK on 2008-07-23
Aha! Excellent little tutorial there, very many thanks for that!

One thing I am a little confused about (Not in the tutorial, in other replies) is how people don't seem sure this could work. I'm rather new to Linux, but from what I seen and done already, I cant see how this particular thing cannot be done. Perhaps my explanations have been lacking, so Ill try again:

I have configured my trackball in xorg.conf, according to information that I have gained on these forums. Having edited the file, I saved it, logged out and back in, and my new mouse settings are loaded. I am able to do this for different mice/trackballs whenever I need to.

What I am proposing is to duplicate the xorg.conf I have now, and change only the mouse settings in the duplicate(s). Surely then, if I copy a duplicate xorg.conf over the original and log out/in, the new mouse settings will have been loaded. This isn't much different to configuring the mouse settings and saving the file, so why wouldn't it work?

Anyway, many thanks to those who have replied, and especially to ConMan318 for that little tutorial.

Regards

Max

---

### Post by ConMan318 on 2008-07-23
I see no reason why this would not work.  If you can manually swap the file and log out/back in and have it work, then that script should most definitely work.  Anything you can do manually can be done with a script, simple as that.  It's just a matter of figuring out what commands are being executed when you are doing things manually, and then coding those.

If you have any questions (i.e. something doesn't work, which it should) post back here; I've got it bookmarked.  And good luck!

---

### Post by MaxVK on 2008-07-24
Unfortunately the script does not seem to work! It runs okay, and the machine logs out as expected, but the xorg.conf is not changed (The filenames are all correct). I'm wondering if this would have something to do with permissions on the xorg.conf since I have to *'sudo gedit'* when I want to edit and save the file.

Ill have another go when I get home again, perhaps adding sudo to the script or even just using the same commands in the terminal and seeing if an error is thrown up.

Max

---

### Post by ConMan318 on 2008-07-24
Sorry!  Forgot all about that, but it's an easy fix.  Just run:
```

sudo chown **yourUsername** xorg.conf

```

This will change the ownership of the file from root to you.  This shouldn't cause any security issues really, since only your account will have access to it.

But after that it will definitely work.

---

### Post by MaxVK on 2008-07-24
Ah! Nice one! Thanks for that!

Regards

Max

---

