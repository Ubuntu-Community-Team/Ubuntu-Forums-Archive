---
title: "How do I  Install ThunderBird and Kompozer?"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by bilbo.san on 2008-05-02
Hello!

I just installed Ubuntu, and I have no Idea on how to install stuff on it.
I was reading that it should be through the 'Synaptic' or the 'Terminal'
But how... I wanted to install 'Mozilla Thunderbird' through Synaptic, but I see several Thunderbirds on the list and do not know which to select... the same with Kompozer HTML editor.

Can you help me?
And how can I get familiar with 'Terminal' commands?
Thanks

b.

---

### Post by bilal.17 on 2008-05-02
Put this into to the terminal ```
sudo apt-get install thunderbird kompozer
```

---

### Post by Nepherte on 2008-05-02
Let's get yourself familiar with terminal commands rightaway:
```
sudo apt-get install thunderbird
sudo apt-get install kompozer
```
apt-get is the software installer for packages from the online software repositories. to install something you add install after apt-get, if you want to remove something remove. To install software, you will need root privileges, which can be done by adding sudo in front of it (this can be done with all commands btw).

For 99.9% of the commands exist a manual page. To call this manual page just place man in front of a command. For example:
```
man apt-get
```

---

### Post by Het Irv on 2008-05-02
If you want to install Thunderbird through the terminal
```
sudo apt-get install thunderbird
```
it will ask for your password, just type it in, even though it looks like nothing is getting inputed.  That will work.  

If you would rather not use a terminal, Applications->Add/Remove Programs->(dropdown box in top center) all availible applications ->(in search box) Thunderbird

the first result should be the one you want. Follow same steps for Kompozer.


The terminal is not that hard to use, the best way to become familiar with it is try to use it as much as possible.  If you have a problem, most people will give you terminal commands to fix them because it is easyier to type.  It took me about 9 months to become comfortable with the terminal.

---

### Post by bilbo.san on 2008-05-02
Thanks everyone!
It looks like it is not too hard to do. It will take months for me to feel familiar with this coding but looks like fun.

Thanks
b.

---

### Post by Het Irv on 2008-05-02
It might take a while, and it might be tough at times, but if you stick with it, it can be very rewarding.  Alot of what I have learned has translated over to my windows job, it's not command for command, but you learn exactly how the computer handles things (all the stuff Microsoft doesn't want you to know they did wrong).

---

