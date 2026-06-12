---
title: "i have this problem enabling i386 architecture first procedimento f wine installation"
date: 2020-06-02
forum: New to Ubuntu
---

### Post by asxadssd on 2020-06-02
i have this problem enabling i386 architecture first procedimment for wine installation in ubuntu 29.04 i have this problem enabling i386 architecture first procedimento f wine installation <pre><b>pkg-config-dpkghook: </b><font color="#C4A000"><b>aviso</b></font>: Architecture i836 not defined in architecture tables, ignored</pre> that is the hmtl pasted code fromterminal to this buntu forum how do i fix this ?

---

### Post by CelticWarrior on 2020-06-02
Please use code tags when posting commands' results. Go Advanced. click "#" and paste inside.

---

### Post by deadflowr on 2020-06-02
Html is disabled on these forums.
Use [BBCode]("https://ubuntuforums.org/misc.php?do=bbcode")...... (preferably code tags for any terminal outputs as it retains the proper formatting)

That said,
looks like you need to enable 32-bit for dpkg
```
sudo dpkg --add-architecture i386
```

---

### Post by asxadssd on 2020-06-02
my non hmlt eror code is [FONT=Ubuntu Mono, monospace][COLOR=#000000]pkg-config-dpkghook aviso: Architecture i836 not defined in architecture tables, ignored that was my eror how to fix it?[/COLOR][/FONT]

---

### Post by deadflowr on 2020-06-02
> Architecture i836 not defined in architecture tables,
No such architecture exists.
Post back what
```
dpkg --print-foreign-architectures
```
says

---

### Post by CelticWarrior on 2020-06-02
"[FONT=Ubuntu Mono][COLOR=#000000]i836" is an obvious typo... Remove it with:

```
sudo dpkg --remove-architecture i836
```

Now...

Why do you think you need "i386" for Wine? And why do you think you need Wine? Clearly you're just starting in the Linux/Ubuntu world. If your first "instinct" is to run Windows software you're off to a very bad start.

[/COLOR][/FONT]

---

### Post by asxadssd on 2020-06-02
how do i install the amd64 architecture for installing wine ?

---

### Post by asxadssd on 2020-06-02
what do you think aobut this url virtual macihne is usafull for running at all potene in a windows virtual macihe the micorsoft windows os yes or not ? [https://download.microsoft.com/download/2/d/2/2d2f760e-aaa7-4268-9904-b5c0260cfd3b/WinDev2004Eval.VirtualBox.zip](https://download.microsoft.com/download/2/d/2/2d2f760e-aaa7-4268-9904-b5c0260cfd3b/WinDev2004Eval.VirtualBox.zip)

---

### Post by CelticWarrior on 2020-06-02
> **asxadssd said:**
> how do i install the amd64 architecture for installing wine ?

If your hardware is 64-bit and your OS is 64-bit then amd64 IS your architecture all the way. You don't install it.
You may need to install 32-bit support for very specific software, in a 64-bit OS. But the other way around it's NOT possible.

So, instead of asking about cryptic newbie mistakes you've been likely making, why don't you post a question about what you want to do actually? Again, I read mentions of "i386 architecture" (this is the 32-bit architecture) and "Wine" and I wonder what for? Please describe your end goal.

---

### Post by CelticWarrior on 2020-06-02
> **asxadssd said:**
> what do you think aobut this url virtual macihne is usafull for running at all potene in a windows virtual macihe the micorsoft windows os yes or not ? [https://download.microsoft.com/download/2/d/2/2d2f760e-aaa7-4268-9904-b5c0260cfd3b/WinDev2004Eval.VirtualBox.zip](https://download.microsoft.com/download/2/d/2/2d2f760e-aaa7-4268-9904-b5c0260cfd3b/WinDev2004Eval.VirtualBox.zip)

One issue per thread, please.
This is totally unrelated. If you want to do virtual machines there's a LOT to learn first.

---

### Post by asxadssd on 2020-06-02
[COLOR=#000000]what do you think aobut this url virtual macihne is usafull for running at all potene in a windows virtual macihe the micorsoft windows os yes or not ? [/COLOR][https://download.microsoft.com/downl...VirtualBox.zip]("https://download.microsoft.com/download/2/d/2/2d2f760e-aaa7-4268-9904-b5c0260cfd3b/WinDev2004Eval.VirtualBox.zip")

---

### Post by asxadssd on 2020-06-02
my actual quuestio is [COLOR=#000000][COLOR=#000000]what do you think aobut this url virtual macihne is usafull for running at all potene in a windows virtual macihe the micorsoft windows os yes or not ? [/COLOR][/COLOR][https://download.microsoft.com/downl...VirtualBox.zip]("https://download.microsoft.com/download/2/d/2/2d2f760e-aaa7-4268-9904-b5c0260cfd3b/WinDev2004Eval.VirtualBox.zip") or gaming computation potence is my questio yes and what is ts answer ?

---

### Post by CelticWarrior on 2020-06-02
[https://ubuntuforums.org/showthread.php?t=2444661&p=13962247#post13962247](https://ubuntuforums.org/showthread.php?t=2444661&p=13962247#post13962247)

---

### Post by asxadssd on 2020-06-02
what is terinal command to enable i386 arquuitecture and what is the complete step by stpe to install all the softwarei need to make that osibble before trying to enable i386 ar archiitecture ?

---

### Post by asxadssd on 2020-06-02
[COLOR=#000000]what is terinal command to enable i386 arquuitecture and what is the complete step by stpe to install all the softwarei need to make that osibble before trying to enable i386 ar archiitecture ?[/COLOR]

---

### Post by asxadssd on 2020-06-02
[RIGHT]how do i create a booatable windows 10 installation media with a pendrive  in ubuntu 20.04?[/RIGHT]

---

