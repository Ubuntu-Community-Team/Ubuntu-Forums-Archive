---
title: "Need help with more user powers"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by outerspacerace on 2008-08-30
Hi all,

After moving over from Windows XP recently, I don't think I'm correctly understanding how the user system works in ubuntu just yet.

Upon installing ubuntu 8.04 I created a user as prompted but there have been certain tasks (advanced) I'm not able to perform.

The main one so far is when I try to edit the etc/gnome/defaults.list to make vlc the default DVD player for example.

I get an error message saying:

You do not have the permissions necessary to save the file.

I tried making myself a member of the groups root & admin but still have the same problem, however I'm not sure I know what I'm doing there - it seemed logical so I tried it is all.

Any help on this would be much appreciated, I'm used to be being able to do/modify whatever I like in XP so this is frustrating me a little!

Thanks in advance.

---

### Post by mevets on 2008-08-30
run this in the terminal:
```

sudo gedit etc/gnome/defaults.list

```

---

### Post by GepettoBR on 2008-08-30
in the Terminal (or Konsole in Kubuntu), if you type the word "sudo" (SuperUser DOes) before any command, you will run that command as "root" (the administrator account that can do anything, just like your account in Windows). Whenever you do that, you will be asked for your user password. After inputting the password, you can run any command as sudo for five minutes, then you have to input it again. This is a safety feature, and even though it seems like a hassle you'll get used to it in no time.

The power to change anything is exactly what makes Windows unsafe, so you should feel reassured instead of frustrated. The fix for your predicament is very easy, in fact there are two:

a) Type "gksudo* gedit** [path and filename]" in the Terminal to open the file and be able to save changes. Don't type in the **s, they're for footnotes to my post :)

or

b) Right-click the file in Nautilus and select "Open as administrator". However, this Nautilus feature isn't available by default. To obtain it, install the "nautilus-gksu" package (either via System>Administration>Synaptic Package Manager or by typing "sudo apt-get nautilus-gksu" in the Terminal), then log out and log back in.

*gksudo and sudo are the same thing, but gksudo is the one you want to use with graphical programs (everything with a point-and-click interface). Sudo is the one you should use for command-line programs like apt-get.

**Gedit is GNOME's equivalent to Windows Notepad. If you use Kubuntu instead of Ubuntu, replace "gedit" with "kate".

---

### Post by RedSquirrel on 2008-08-30
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by outerspacerace on 2008-08-30
Wow thanks for such quick and informative responses, especially Gepetto! I think maybe I need to find a good place to read up on the terminal now...

Unfortunately however, when I tried mevets suggestion and your first one also it didn't work out.

Both times after typing the code in a blank defaults file was opened up for me. Was I supposed to type the entries I want to change in there? When I did that manually I got an error saying the file could not be found.

I also tried opening another instance of the defaults.list file by browsing to it and changing the entries from totem to vlc there but again it told me I didn't have permission to do so.

---

### Post by RedSquirrel on 2008-08-30
You have to specify a correct path to the file, e.g., an absolute path, starting from / would be:

```
gksudo gedit **[COLOR=Magenta]/[/COLOR]**etc/gnome/defaults.list
```

---

### Post by GepettoBR on 2008-08-30
> **outerspacerace said:**
> Wow thanks for such quick and informative responses, especially Gepetto! I think maybe I need to find a good place to read up on the terminal now...

Unfortunately however, when I tried mevets suggestion and your first one also it didn't work out.

Both times after typing the code in a blank defaults file was opened up for me. Was I supposed to type the entries I want to change in there? When I did that manually I got an error saying the file could not be found.

I also tried opening another instance of the defaults.list file by browsing to it and changing the entries from totem to vlc there but again it told me I didn't have permission to do so.

We're always glad to help! If you find a post useful, please click the little star icon next to that post's quote button and help give us a little ego boost!

As for the blank file, RedSquirrel's suggestion should fix your problem. This has to do with working folders and how Linux organizes the filesystem.

/ is the root directory. It's like C: in Windows, except every other disk is also inside C: instead of on its own directory tree. When you open the Terminal, it defaults to your home folder (/home/username) so if you type, for example, "touch foo.txt" it will create an empty file called foo.txt on /home/username. You can change the working folder with the cd command, but the important thing here is knowing if you're using relative paths or absolute paths.

Absolute paths start with /. They're like typing the full file path in Windows (for example, "C:/Documents and Settings/Paulo/My Videos/Blind Guardian - Another Stranger Me.mpeg"). Relative paths start from your working folder and do not begin with /. So, if my working folder were "Documents and Settings" in the Windows example and I wanted to access the same file, I'd type "Paulo/My Videos/Blind Guardian - Another Stranger Me.mpeg".

If RedSquirrel is right, and you did forget to add the / before etc/gnome/defaults.list, then gedit opened the relative path to /home/your-user-name/etc/gnome/defaults.list instead of simply /etc/gnome/defaults.list. Since that file doesn't exist, it came up as blank.

---

### Post by outerspacerace on 2008-08-30
Awesome!

Red was indeed right and Gepetto cheers again ;)

I'll be referring back to your posts when I have more time for it all to sink in but I do get the basics of what you're saying already, and yes - I did forget the / in the first instance.

Funny thing is though I accomplished what I wanted, in that vlc is now the default player, it still doesn't behave how I'd like.

When I insert a DVD movie it begins playing the movies as totem did, it even detected a motion menu as a movie and played through it's 45sec odd length.

I was hoping it would open up like say Power DVD under windows, letting me select scenes, click on extras etc. To do this I have to go file>open disc or open directory for it to "sense" it's an actual authored DVD movie with features, rather than simply begin playing the first movie stream.

I guess that's a something to look into or maybe a post in another section though!

Anyway cheers again, at least now I don't have to close totem first every time, it isn't the best for DVD playback at this point in time.

---

### Post by aysiu on 2008-08-30
While it's great that you're learning a bit about using *sudo* (or actually *gksudo* in the case of Gedit - more details [here](http://www.psychocats.net/ubuntu/graphicalsudo) about *sudo* v. *gksudo*), I think you're going about this the wrong way.

If you're editing the default applications within /etc, you're changing the defaults for all new users, not just your current user. I think you should be able to change the default application within Places > Home > Edit > Preferences or in System > Preferences > Preferred Applications.

You shouldn't need to edit system files or use the terminal.

---

### Post by outerspacerace on 2008-08-31
Perhaps you're right - I shouldn't have to edit system files or use the terminal for something like this, though in 8.04 it appears you do need to.

I'd already tried the methods you spoke of prior to posting and vlc isn't an option in the first way (though after editing the defaults.list it does show up there) nor the second method... which by the way would probably have vlc controlling other files types (such as music etc) if it was possible.

I was more specific in my needs in that I only really wanted vlc to be the default program for dvd playback, which now I have :)

Good point to note about the method I used controlling other users though!

Actually a method here; [http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy) seems to be harder to implement but I think it may stop the changes affecting all users?

I haven't tried it as I'm the only real user of ubuntu here so far.

---

### Post by aysiu on 2008-08-31
You're absolutely right. Hardy took that flexibility away.

Your best bet is the [Ubuntu Guide](http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_make_VLC_open_when_you_insert_a_DVD) fix.

It looks complicated, but you can just copy and paste the commands.

---

