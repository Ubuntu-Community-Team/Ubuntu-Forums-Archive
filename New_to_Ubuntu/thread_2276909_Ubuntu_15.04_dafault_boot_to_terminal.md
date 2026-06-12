---
title: "Ubuntu 15.04 dafault boot to terminal"
date: 2015-05-05
forum: New to Ubuntu
---

### Post by Trandre on 2015-05-05
Hi, I haved installed a server 15,04, I installed the graphic interface to be enable the wifi etc. But now I want to revert to default terminal on open. 

Following threads I should enter the "Text" in the file /etc/default/grub like below
Then i did sudo update-gnome and the sudo reboot.

But newertheless it starts up in GUI, what am I doing wrong?

 [IMG]http://ubuntuforums.org/asset.php?fid=258350&uid=1018286&d=1430861172[/IMG]

---

### Post by Bashing-om on 2015-05-05
Trandre; Hello;

Your edit to '/etc/default/grub' looks good; the fault I see:
> 
Then i did sudo update-[color=red]gnome[/color] and the sudo reboot.

The command to propagate the change to the system should be:
```

sudo update-grub

```

Try that and advise on results .

[INDENT][INDENT]it's them there little things
[/INDENT][/INDENT]

---

### Post by Trandre on 2015-05-06
Hi Again, I did the sudo update-grub, but it still boots into gui. It does stop for some seconds on the terminal view to prompt for username, but then i openes gui. 

It looks like a later process is turning it into graphic after it has booted into terminal. Does this make sense?

---

### Post by Bashing-om on 2015-05-06
Trandre; Hey; 

> 
It looks like a later process is turning it into graphic after it has booted into terminal. Does this make sense?

Maybe ? ..What GUI did you install ? (DE) , and how are you set up to start it ? What config file(s) are at play here .

I am always interested in the startup processes, and this too might be a learning adventure.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by sandyd on 2015-05-06
Ubuntu 15.04+ needs to disable gui via systemd

Run```

sudo systemctl enable multi-user.target --force
sudo systemctl set-default multi-user.target
```

---

### Post by Bashing-om on 2015-05-06
@sandyd; Great !

& to see ya !

Yeah, systemd is going to be different. This is not intuitive at all as to what it effects. Youch.
Getting past time for homework.


[INDENT][INDENT]the times they are achang'n
[/INDENT][/INDENT]

---

### Post by Trandre on 2015-05-14
I had to downgrade to xubuntu, because hw capability. Then the default open in CLI mode work suddenly.

&#128077;

---

### Post by Bashing-om on 2015-05-14
Trandre; Great;

The right tool for the job.

[INDENT][INDENT]we just keep on keep'n on
[/INDENT][/INDENT]

---

