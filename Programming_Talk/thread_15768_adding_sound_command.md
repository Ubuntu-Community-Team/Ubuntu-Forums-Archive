---
title: "adding sound command"
date: 2005-02-16
forum: Programming Talk
---

### Post by csindone on 2005-02-16
I am new to linux. I have a program I run called mail-notification. There is a section for commands:

1. Mail reader: firefox [http://gmail.com](http://gmail.com)
2. When new mail arrives:
3. When all mail is read

As you can see I use Gmail and have added the command: firefox [http://gmail.com](http://gmail.com)

I would like to play a .wav file in the command When new mail arrives:

the .wav file is located in /home/chris/ problem is I don't know the command to play a sound

---

### Post by gogodidi on 2005-02-16
are you asking to play a sound file when you receive a new email in your gmail account while using firefox?

I dont think there is anything that can be done about that, but if you mean thunderbird.. then... there is a section there, somewhere where you can change that...

---

### Post by csindone on 2005-02-16
[QUOTE=gogodidi]are you asking to play a sound file when you receive a new email in your gmail account while using firefox?

I dont think there is anything that can be done about that, but if you mean thunderbird.. then... there is a section there, somewhere where you can change that...[/QUOTE]

No I am looking for the command to play a sound file, with some Linux it's play or splay, but neither seems to work

---

### Post by ryu kun on 2006-09-11
> **csindone said:**
> I am new to linux. I have a program I run called mail-notification. There is a section for commands:

1. Mail reader: firefox [http://gmail.com](http://gmail.com)
2. When new mail arrives:
3. When all mail is read

As you can see I use Gmail and have added the command: firefox [http://gmail.com](http://gmail.com)

I would like to play a .wav file in the command When new mail arrives:

the .wav file is located in /home/chris/ problem is I don't know the command to play a sound

You should install esound-clients first:

```
sudo apt-get install esound-clients
```

Then you can use this command to play a sound:

```
esdplay /home/filename.wav
```

---

### Post by CortalUX on 2007-03-21
Although noting the date on this thread, I think some good information could be contributed for future reference, which would have especially helped me.
For one, there is now a shell script released under the GPL2 licence [http://matthew.ruschmann.net/blog/Linux/gnome-gmail-1.1.html](http://matthew.ruschmann.net/blog/Linux/gnome-gmail-1.1.html) which allows you to have gmail as your default mailer, rather than firefox pointing to the site in all cases... so you can open a specific message in mail-notify upon recieving a mail, rather than having 'firefox www.gmail.com' in your gnome preferred applications or going through evolution.
The other thing, is that in feisty at least, the 'play' command comes in the 'sox' package from the universe repository [esounds didn't work for me].
So if the repository is enabled you can do this in a terminal.
```
sudo apt-get install sox
```
And then use this example to play a sound:
```
play ../../home/<USER>/<PATHTOSOUND>/sound.wav
```
Sorry if this is obvious, but I think it can be a good reference when you find information through searching the ubuntu forums.

---

