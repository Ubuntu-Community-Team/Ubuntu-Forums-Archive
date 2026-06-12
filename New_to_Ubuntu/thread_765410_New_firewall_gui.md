---
title: "New firewall gui?"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by kansasnoob on 2008-04-24
Wow, how lame am I? I just now found out that the system I'm using has something I didn't know it had.

In every install/upgrade I've done with 8.04 I've still just relied on the Firestarter gui to set-up my iptables.

I'm lazy. I like simple stuff. Are the settings I make in Firestarter still valid?

I know I had Firestarter working properly with iptables in 7.10. Now what?

Ufw has no "interface"!

Are we going backwards? Back to "command line" only?

Now, I figured out long ago in Gutsy that there was no need to edit "sudoers" to allow Firestarter to open automatically in the kicker panel, but now I don't think I even have a firewall running!

That bothers me!

HELP! And keep it simple.

---

### Post by swoll1980 on 2008-04-24
Iptables is the firewall it is running by default unless you turned it off

---

### Post by Technoviking on 2008-04-24
I understand that ufw would be easier to config with a gui, but it is a very simple program to use from the command line

Turn on the firewall
```
sudo ufw enable
```
Turn off the firewall.
```
sudo ufw disable
```
Allow all connections by default.
```
sudo ufw default allow
```
Drop all connections by default.
```
sudo ufw default deny
```
Current status and rules.
```
sudo ufw status
```
Allow traffic on port <port>.
```
sudo ufw allow <port>
```
Block port number <port>
```
sudo ufw deny <port>
```
Block IP address.
```
sudo ufw deny from <ip>
```

For example to block all traffic except for ssh do the following.
```
sudo ufw default deny
sudo ufw allow 22

```

I will see if a Ubuntu Brainstorm has a GUI for UFW as an idea.

Mike

---

### Post by yaztromo on 2008-04-24
Is ufw just another frontend for iptables?

---

### Post by Technoviking on 2008-04-24
Vote it up at Ubuntu Brainstorm
[http://brainstorm.ubuntu.com/idea/22/](http://brainstorm.ubuntu.com/idea/22/)

---

### Post by Technoviking on 2008-04-24
More info on ufw:
[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

---

### Post by noynac on 2008-04-24
> **Mike said:**
> More info on ufw:
[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

Thanks for the link. If I understand that site correctly, disabled is the default for ufw. I ran 'sudo ufw status' and it said "firewall not loaded." Clearly this is something I need to study up on.

---

### Post by Paqman on 2008-04-24
I though ufw was just a CLI tool for managing iptables? If you want a GUI, just use Firestarter. They both do exactly the same thing.

---

### Post by kansasnoob on 2008-04-24
Well, maybe I did a bad job of explaining myself, but I have installed Firestarter on all of my 8.04's and I'm freaking a little bit. I can't find any log of activity for Firestarter or ufw!

I'd gotten used to the idea that i didn't need to see what was going on as it happened but now it looks like I've been WIDE OPEN for a few days because of of my own stupidity.

I don't think the Firestarter gui is working properly with ufw. In fact it may have been disabling ufw?

---

### Post by Paqman on 2008-04-24
> **kansasnoob said:**
> 
I don't think the Firestarter gui is working properly with ufw. In fact it may have been disabling ufw?

Firestarter doesn't talk to ufw, it talks to iptables (just like ufw does) They're both tools for configuring iptables. One is a GUI, the other is CLI.

When you say you "can't find any log of activity", what do you mean? That there are no logs in Firestarter?

---

### Post by kansasnoob on 2008-04-24
So, is my Firestarter gui interfering with the operation of ufw?

This is one of those odd things that makes you wonder why all open sourcers can't just work together!

Or should I open the terminal every time I start my computer and make sure my firewall is started?

---

### Post by Paqman on 2008-04-24
> **kansasnoob said:**
> So, is my Firestarter gui interfering with the operation of ufw?


Have you even touched ufw though? If so, what changes did you make?

I'd be surprised if they hadn't tested Firestarter with ufw to make sure they weren't interfering with each other.

---

### Post by kansasnoob on 2008-04-24
"When you say you "can't find any log of activity", what do you mean? That there are no logs in Firestarter?"

Yes Paqman,

I'd learned how to log the activity to and from my network using Firestarter. I know that Firestarter works on top of iptables. You'll notice that I chalked the problem up to my own oversight. I should have had this figured out a week ago.

The most obvious solution for me is to remove ufw, make sure that iptables and all libraries are installed and then reinstall Firestarter.

Then I'll learn how to properly use ufw.

This was pointed out in Ubuntu's build up to 8.04. My bad! I didn't do my homework!

---

### Post by kansasnoob on 2008-04-24
Well, I ran thru a full restart and everything showed "fail" when firestarter came up.

But I've tried physically starting firestarter and it begins logging events like it should.

I just think ufw and firestarter are having a pi$$ing contest at this point.

---

### Post by kansasnoob on 2008-04-24
Well, it appears that iptables goes to the default with both ufw and firestarter installed.

I think that synaptic should force one to be removed when the other is installed!

At this point i think the safest bet is to NOT install firestarter and make sure ufw is on:

sudo ufw enable

and just leave it alone unless you have a complicated  network.

I don't like it though!

---

### Post by gaiterin on 2008-05-26
Hello.
I made a GUI in Python.
You can download it at:
[http://code.google.com/p/gui-ufw/](http://code.google.com/p/gui-ufw/)
To install follow the instructions of the file installation.
A greeting.

---

### Post by mister_pink on 2008-05-26
Err, just tried to check out the svn code and got an empty folder... But surely a gui to a script to a program is a bit of a odd way of doing things?

Edit: Ignore the svn thing, I just downloaded the tar ball instead...

Edit2: Does look nice and simple though

---

