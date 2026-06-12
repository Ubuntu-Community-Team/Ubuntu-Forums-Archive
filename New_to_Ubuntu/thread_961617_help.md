---
title: "help"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by davellew69 on 2008-10-28
Hi can anyone shed light on this sudo stuff? I`m trying to install programs, and my head is spinning,  I`m not knocking ubuntu , but it was so easy installing using windows.

how do enter in the terminal( I assume that were I do it )

also I`ve installed a printer but no joy,I have partitioned the hard drive for dual use , can this affect the printer not working.

any help is welcome ,, but please keep it simple

---

### Post by jerome1232 on 2008-10-28
Once you learn how the packaging sytem works you'll think it's hard to install stuff in windows :)

There are two gui's for installing programs, the easy one is Applications->Add/Remove

For more advanced features, and access to more programs, use synaptic System->Administration->Synaptic Package Manager.

Just sort through the list and mark programs you want for installation.

This might be of help to you. [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

No dual booting won't affect the printer.
What model printer is it? Most printers I've used I just plugged in and they were ready to go.

---

### Post by dracayr on 2008-10-28
the terminal is in Applications&#8594;accesories&#8594;terminal. If someone says "enter blablabla in a terminal", he means typing "blablabla" in a terminal and hitting the enter key. The sudo command gives you adminstratory rights. After a while you'll love the way programs are installed in ubuntu. It doesn't have to be via the terminal, you can also use System&#8594;Administration&#8594;Synaptic package manager. You have a list of programs to choose from... Isn't that better than going to an internet site (which sometimes requires some skill with google) and downloading a file to execute it?
A dual boot setup does not affect the printer.

EDIT: Please use more descriptive topic titles... As you may have noticed, about everyone is looking for "help" here

dracayr

---

### Post by davellew69 on 2008-10-28
cheers mate i`ll try, I guess its just a case of being patient... any way the printer is a lexmark x3470

---

### Post by davellew69 on 2008-10-28
oh man i`m confused  tried syptatic system manager...no luck just error message, and terminal is usless i enter password on nothing?

---

### Post by jerome1232 on 2008-10-28
I was kind of thinking so, aside from lexmark making bad printers they have horrible Linux support, all of my printers are hp/epson and they work out of the box so I can't really help you with that one.

---

### Post by jerome1232 on 2008-10-28
> **davellew69 said:**
> oh man i`m confused  tried syptatic system manager...no luck just error message, and terminal is usless i enter password on nothing?

What error message? 

Yes a terminal will not echo your password back, just type it in and press enter.

What is it your actually trying to do? If you are trying to get that printer to work I would suggest either making a new thread titled how to get lexmark x3470 to work, or reporting you first post in the thread requesting a title change (put something like request title change to 'how to get a lexmark x3470 to work'

---

### Post by davellew69 on 2008-10-28
i dont understand this sudo stuff, it asks for a password , i enter user paswword and nothing happens? how do i enter into terminal if this keeps happening , i
I like ubuntu, but to install is a nightmare

---

### Post by davellew69 on 2008-10-28
the error message in syptic manager thing is e;dpkg interupted

---

### Post by jerome1232 on 2008-10-28
I still don't understand what it is your trying to do, are you in a livecd at the moment trying to install Ubuntu? If so there should be an 'install' icon sitting on your desktop that you double click on to start the install process.

If your just trying to install some programs just use add/remove... or synaptic, there's a huge database of programs in there. There's no need for the terminal. If you can tell us what the error is we can help out but if I don't know the error then I don't know what's wrong.

edit: Okay that error actually tells you what to do, that means you interputed it while it was working before so you actually need to goto a termianl to fix this.
open a terminal and try this (from memory but your error should tell you the exact command)
```
sudo dpkg --configure -a
```

---

### Post by m_duck on 2008-10-28
When you are typing your password into the terminal, it will not show a response. This is for security, but if you just type your password and press enter, it will work.

---

### Post by davellew69 on 2008-10-28
not in live cd for example to install realplayer, im asked to download the program, the enter sudo install real player, does that help, the error message is e dpkg interrupted

---

### Post by davellew69 on 2008-10-28
nope i press enter and nothing happens

---

### Post by zakirs on 2008-10-28
u r trying to install something in live cd. .. ?

---

### Post by jerome1232 on 2008-10-28
I guess you didn't catch my edit. This command should get you back up and running with apt-get
```
sudo dpkg --configure -a
```

---

### Post by davellew69 on 2008-10-28
okay the syptic thing works now, thank you, just trying to get the webcam and printer to work...oh well one day maybe

---

