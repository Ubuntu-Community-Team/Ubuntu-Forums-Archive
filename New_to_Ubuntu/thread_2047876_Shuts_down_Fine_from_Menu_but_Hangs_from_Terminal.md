---
title: "Shuts down Fine from Menu but Hangs from Terminal"
date: 2012-08-25
forum: New to Ubuntu
---

### Post by Andavane on 2012-08-25
In my small Thinkpad X121e with amd chip the machine shuts down fine from the top-right menu, but when I try sudo halt, it all *seems* to shut down fine, then I get this:
[http://flic.kr/p/cYtgjw]("http://flic.kr/p/cYtgjw")

& it doesn't go away.

When I go to Terminal and go sudo restart I get this:

[http://flic.kr/p/cYtin1]("http://flic.kr/p/cYtin1")

I am puzzled by both.

Precise

---

### Post by BDNiner on 2012-08-25
restart command is used to restart a particular process. If you want to restart the computer try
```

sudo reboot

```
What happens if you try:
```

sudo poweroff

```

---

### Post by Bashing-om on 2012-08-25
Andavane;

  What version are you running? In my 10.04 proper terminal commands to reboot:
```
sudo shutdown -r now

```
shutdown:
```
sudo shutdown -P now
```

[INDENT]HTH <==BDQ

[/INDENT]

---

### Post by irv on 2012-08-25
Looks like you are using 12.04, that's what I have.
What I use to shutdown and power off is
```
sudo shutdown now
```
type in my password and down it goes.
This way it shuts down all the processes and cleans up any loose ends. It is the same as doing a shutdown from the menu.
If you want to do a restart just add the -r option

---

### Post by Andavane on 2012-08-27
> **BDNiner said:**
> restart command is used to restart a particular process. If you want to restart the computer try
...
What happens if you try:
```

sudo poweroff

```

 Much the same, mate. Very similar to last pic.

> **Bashing-om said:**
> Andavane;

  What version are you running? In my 10.04 proper terminal commands to reboot:
```
sudo shutdown -r now

```
shutdown:
```
sudo shutdown -P now
```

[INDENT]HTH <==BDQ

[/INDENT]
I didn't try these as am in 12.04 32-bit version

> **irv said:**
> Looks like you are using 12.04, that's what I have.
What I use to shutdown and power off is
```
sudo shutdown now
```
type in my password and down it goes.
This way it shuts down all the processes and cleans up any loose ends. It is the same as doing a shutdown from the menu.
If you want to do a restart just add the -r option

Yes mate but it didn't.
When I do, I get this: [http://flic.kr/p/cZMyT3]("http://flic.kr/p/cZMyT3")
Something about not being able to get the system bus.
Yet when I shut down from the dropdown menu, bingo and all is hunky-dory.
Weird, huh?

---

### Post by Bashing-om on 2012-08-27
andavance;

 Here is a thought. Do you have any scripts not exiting properly or any open ssh extensions ? see the man page for what might be going on:
[http://manpages.ubuntu.com/manpages/precise/man1/dbus-launch.1.html](http://manpages.ubuntu.com/manpages/precise/man1/dbus-launch.1.html)

[INDENT]hth <==BDQ

[/INDENT]

---

### Post by Andavane on 2012-09-02
> **Bashing-om said:**
> andavance;

 Here is a thought. Do you have any scripts not exiting properly or any open ssh extensions ? see the man page for what might be going on:
[http://manpages.ubuntu.com/manpages/precise/man1/dbus-launch.1.html](http://manpages.ubuntu.com/manpages/precise/man1/dbus-launch.1.html)

[INDENT]hth <==BDQ

[/INDENT]

Well mate, scripts and man pages are something I haven't much clue about I'm afraid, although I'm happy to learn what I can. Man page = like 'The Manual', yes? Presumably scripts are strings of those command line you see in the terminal when updating as such. 

One thing I can say is that in this installation I installed m drop thru the terminal. It's a 64-bit machine but I installed 32-bit Ubuntu here for a reason I'm about to post about. I typed this:

> 

cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86" | tar xzf -
        

64-bit:

cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86_64" | tar xzf -

and I start dropbox with this command: > ~/.dropbox-dist/dropboxd

O stop it by rigt-clicking on the symbol in the bar at the top and going "quit".

So I tell you this, in case you think this has anything to do with it.

Still, everything shuts down perfectly and very quickly when I do it from the menu but delays and hangs if I use the terminal. So I am left with holding down the start/stop button until it cuts out and I really don't like having to do that.

PS: What does the "hth <==BDQ" mean?

---

