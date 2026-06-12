---
title: "Phisical attack by USB device (and btw, ps/2)"
date: 2009-11-25
forum: Recurring Discussions
---

### Post by LimCore on 2009-11-25
Following scenario - unlikely, but technically possible;

Trusted user (but not fully trusted admin) brings in his USB disc.
He connects it to box, gets his files from it.
Later admin comes over (and user steps aside for a moment).
Admin logs into secure console alt+ctrl+f1 perhaps raw-mode by SysCtrl etc,
and then he logs in as admin, su to root and does some installations.
Admins logs out.

Now the computer is owned.

This is quite tricky, but possible probably.

How? 

The USB device also worked as a keyboard-device, the "keyboard" was carefully pre-set to emit set of keypresses, like say:
  bash /mount/disc1/install_backdoor.sh & 2> /dev/null
with 30 seconds delay. If admin was not watching the monitor closely, or there was much output in his bash session, then perhaps the attack could be even not noticible with a bit of extra work. Or at least not obvious what happened.

Fix? 

Just disallow attaching any more USB keyboards/mouses/inputs then the original ones available when first booted.

How to implement that?

---

### Post by scorp123 on 2009-11-26
> **LimCore said:**
>  Later admin comes over ...  That's the part where it gets unrealistic :D

Admin coming over ...** to a user???!!!** ;)  Nope. Admins are as lazy as it can get and they'd use SSH remotely.

Even if the user simulates a network problem (so SSH can't work anymore) a real admin tasked with oh-so-important things like keeping his Facebook page up-to-date and reading Slashdot --oh and yeah, we even have time to patch the systems and what not in between-- wouldn't be too much in a hurry if he hears that the user can still get data off the disk with a USB stick ... in that case the problem can't be so dramatic.


> **LimCore said:**
>  How to implement that?

Not possible IMHO. Because I am not typing on the stick, so it can't emit any keystrokes. If anything then you'd have to manipulate the keyboard itself. And when it comes to that you can save yourself the hassles and just order one of the existing solutions: 

[http://www.keyghost.com/USB-Keylogger.htm#plug](http://www.keyghost.com/USB-Keylogger.htm#plug)
[http://www.keylogger.com/hkkeyboard.htm](http://www.keylogger.com/hkkeyboard.htm)
[http://www.keylogger.com/hkstandalone.htm](http://www.keylogger.com/hkstandalone.htm)


I have had to use those things myself to help my employer find a mole who was leaking secret information to the press and to our competitors ... And once somebody returned me the favour and I found one of those things attached on a computer that I use regularly ...

**Since then I don't trust other people's keyboards and I insist bringing my own ... ** And yes, since then I double-check the PS/2 and USB connectors for any "funny" plugs, cables and sticks that shouldn't be there ...

---

### Post by wilee-nilee on 2009-11-26
> **scorp123 said:**
> That's the part where it gets unrealistic :D

Admin coming over ...** to a user???!!!** ;)  Nope. Admins are as lazy as it can get and they'd use SSH remotely.

Even if the user simulates a network problem (so SSH can't work anymore) a real admin tasked with oh-so-important things like keeping his Facebook page up-to-date and reading Slashdot --oh and yeah, we even have time to patch the systems and what not in between-- wouldn't be too much in a hurry if he hears that the user can still get data off the disk with a USB stick ... in that case the problem can't be so dramatic.




Not possible IMHO. Because I am not typing on the stick, so it can't emit any keystrokes. If anything then you'd have to manipulate the keyboard itself. And when it comes to that you can save yourself the hassles and just order one of the existing solutions: 

[http://www.keyghost.com/USB-Keylogger.htm#plug](http://www.keyghost.com/USB-Keylogger.htm#plug)
[http://www.keylogger.com/hkkeyboard.htm](http://www.keylogger.com/hkkeyboard.htm)
[http://www.keylogger.com/hkstandalone.htm](http://www.keylogger.com/hkstandalone.htm)


I have had to use those things myself to help my employer find a mole who was leaking secret information to the press and to our competitors ... And once somebody returned me the favour and I found one of those things attached on a computer that I use regularly ...

**Since then I don't trust other people's keyboards and I insist bringing my own ... ** And yes, since then I double-check the PS/2 and USB connectors for any "funny" plugs, cables and sticks that shouldn't be there ...

Diabolical.

---

### Post by OpSecShellshock on 2009-11-26
The user is able to move files off of a work computer and on to a personally-owned usb storage device? There's your security hole right there. In fact, what are those files doing on the local machine instead of being kept on a share drive?

In any case, I think you can prevent users from being able to mount external storage altogether. Also, the user would have to know what they were doing, and the admin would have to be careless enough not to remove everything before doing administrative work. And as someone said before, they'd be more likely to do installations remotely through an automated process from a central repository to the entire enterprise network.

---

### Post by Bjalf on 2009-11-27
The biggest security hole is physical access to the computer.

What is to keep me from booting the computer from a CD or USB stick filled with hacking tools, and then give myself permanent admin rights? Not a BIOS password, those are easily cleared with a screwdriver.

And speaking of screwdrivers, if I wanted to install a hardware keylogger that was not visible from the outside of the case ...

---

### Post by scorp123 on 2009-11-27
> **Bjalf said:**
>  What is to keep me from booting the computer from a CD or USB stick filled with hacking tools, and then give myself permanent admin rights?  LDAP or AD. If a user's password and account info isn't stored locally then there isn't much he can manipulate locally. BTW, if a user has *that* level of knowledge he'd most likely be admin anyway.

In the areas where we really really want to restrict users they get Sun Ray Ultra-ThinClients onto their desks. No local OS. No local memory. No local disk whatsoever. Nothing to manipulate. ;)

---

### Post by iponeverything on 2009-11-27
I agree that when someone has physical access to machine, there is very little you can do. 

- have the OS reload from network after every user is way that I have see some NetCafé's do it.

- have teeth in you user policies. 
Many USG user violations will get (depending on severity) 1 warning. After that things get pretty bad, pretty quickly.

---

### Post by Bjalf on 2009-11-27
> **scorp123 said:**
> LDAP or AD. If a user's password and account info isn't stored locally then there isn't much he can manipulate locally. BTW, if a user has *that* level of knowledge he'd most likely be admin anyway.

Good point.

:)

---

### Post by bodhi.zazen on 2009-11-27
If a would be cracker has physical access they own the machine.

Bringing your own keyboard is an interesting idea, but I am not convinced it helps you much.

IMO the bottom line :

1. Do not allow physical access.

2. Do not enter passwords or log into untrusted machines on untrusted networks.

When I use my netbook on untrusted networks I have my firewall enabled, aparmor watching network aware applications, and do not log into anything outside of ssl and ssh.

---

### Post by scorp123 on 2009-11-27
> **bodhi.zazen said:**
>  Bringing your own keyboard is an interesting idea, but I am not convinced it helps you much. Imagine this:

You're at customer or partner company with whom you have a somewhat difficult relationship. Some question about a rather hot topic comes up and you'd need to urgently check your mails (e.g. to see if your boss has taken care of the issue that has been brought up ...). And so the dialogue goes:

- "Hmmm, I'd need to check my mails ... "
- "Oh, of course. Sure. No problem. Pleeeeaaaazze, feel free to use ***this*** keyboard to login into your web mail account .... "

==> That's what I mean when I say "I don't trust keyboards I didn't bring myself". And yes, above dialogue happened to me for real ...

Their corporate policies forbid non-employees to bring their own laptops into the company, so I could not use my own laptop. But I definitely didn't trust that sleazy guy and his insistence on using ***that*** one particular keyboard. Whenever I said something like "Uhhmmm, no problem, I'll write my mail from over there ... " he had like a dozen or so excuses why this would not be possible. All of a sudden every other PC in the room had "Network problems" ... And when I offered "to check if the network cable is loose" (= see if there is a keylogger on that PC he wants me to use) he all of a sudden insisted "Oh, no, don't go down there, too much dust and dirt. This PC works tip top. Just sit down and use it .... " 

I definitely didn't use it. I didn't trust this guy and that PC he wanted me to use not even one little bit.

---

### Post by bodhi.zazen on 2009-11-27
Wow, I mean just wow ...

---

### Post by scorp123 on 2009-11-27
> **bodhi.zazen said:**
> Wow, I mean just wow ... Yeap. That's what I call "interesting work atmosphere" ... :D   With "partners" like that ... who needs enemies? :D

---

### Post by BkkBonanza on 2009-11-27
Regarding the original post, I think it is possible to make a USB device that negotiates as both a mass storage device and a HID (keyboard). It would require writing low level code for the usb stick's processor, and a generic usb processor rather than one of the more typical dedicated usb chips. All told I think there would be easier ways to capture or inject commands using software.

And regarding carrying a keyboard around... that's just hilarious. What makes you think that would prevent a key logger from working? They aren't just hardware dongles you know. In fact, it's far more likely to be software based. If I was that worried about a key logger at a place I was visiting I'd be much better off waiting to check my mail somewhere else.

Sometimes these forums are pretty bizarre.

---

### Post by scorp123 on 2009-11-28
> **BkkBonaza said:**
>  All told I think there would be easier ways to capture or inject commands using software.

> **BkkBonaza said:**
>  And regarding carrying a keyboard around... that's just hilarious. What makes you think that would prevent a key logger from working?  Because underneath that "keyboard" I'm carrying around happens to be my laptop :D

OK, maybe I should rephrase what I wrote above. It shouldn't be "I always carry my own keyboard around" .... It should rather be "I always have my laptop with me" and "You can't trust other people's computers". This one "I don't trust a keyboard I didn't bring myself" though doesn't sound too bad. But never mind.

USB-stick like keyloggers exist and they are being used. So instead of reinventing the wheel and the fire and getting your own USB creation to work you can use the existing solutions. 


> **BkkBonaza said:**
>  If I was that worried about a key logger at a place I was visiting I'd be much better off waiting to check my mail somewhere else.  Exactly. What's "bizarre" about that?

---

### Post by 3rdalbum on 2009-11-28
You mean "local attack by USB device", not "physical attack". I can't imagine how a flash drive can cause much of an injury, even if you hurled it at someone's face.

---

### Post by BkkBonanza on 2009-11-28
> **scorp123 said:**
> 
USB-stick like keyloggers exist and they are being used. So instead of reinventing the wheel and the fire and getting your own USB creation to work you can use the existing solutions. 

...

Exactly. What's "bizarre" about that?

But the original post isn't about a USB key logger. He's talking about a USB device that looks like a memory stick but inserts some commands without the admin user knowing by forcing them in as if a keyboard. Kind of the opposite of a key logger. Or maybe I read it backwards... I think his idea was that it would detect when root had been achieved and could sneak in a few commands. Perhaps a round about social engineering trick.

Now that you clarified about using a laptop and not carrying a keyboard around it all doesn't sound as bizarre. Oh well, all in good fun.

---

### Post by scorp123 on 2009-11-28
> **BkkBonaza said:**
> But the original post isn't about a USB key logger. I know. What he imagines is some sort of "keycode injection" device. But I doubt that it would work. See my comment back there. For one thing: How can that device know when exactly I am typing on the keyboard or not? That could only work if it were a keylogger too. And for that it needs to be attached to the keyboard as well.

So if the goal is to gain "root" priviledges, then the easiest thing would be to pretend something is broken (as OP suggested), have an admin come over and then trick the admin to type in the "root" password on a specially prepared keyboard (e.g. one with a keylogger inside or attached on the other end). Bingo.

That's why I brought up keyloggers. Simulating a keyboard and *injecting* harmful code sequences via another device would probably be next to impossible. But solutions for *intercepting* USB packets that pass through and filtering for interesting strings (e.g. passwords) already exist ...

See what I mean?

> **BkkBonaza said:**
>  He's talking about a USB device that looks like a memory stick but inserts some commands without the admin user knowing by forcing them in as if a keyboard.  Intercepting the "root" password would be more "profitable" from an intruder's point of view. 

Let's suppose the "bad code injection" worked as described: I walk over to the user, I type in my "root" password, and from that second onwards all hell breaks loose ... and then I just walk home without being suspecting that something fishy is going on???? **Highly unlikely.**

Intercepting the "root" password with a keylogger would be far more subtle and sneaky. I walk over to the user. I login as "root" and fix whatever problem the user had. Nothing strange happens ... yet. I walk home. User stays to "clean up the mess, backup some files" ... Whatever. And when nobody is watching he unplugs the keylogger and puts it into his pocket and goes home too. And then at home --where nobody else is watching him-- he can analyse the keylogger's memory, filter out the passwords it has logged ... 

From now onwards whenever he thinks nobody is watching him he can login as "root" and do a lot of interesting things ... Plant backdoors. Plant trojans. Open up ports in the firewall. Install reverse SSH daemons. Snoop the traffic. Manipulate files ...

Insider jobs are as sneaky and "deadly" to a company as it can get. Depending on how cautious this user is it would probably take weeks or even months to discover him.

That's what I mean. Injecting bad keycodes --if it were possible the way OP imagines-- would be way too obvious and highly shortsighted. You destroy one PC. Oh dear -- big deal. Intercepting the keycodes of somebody typing in a few interesting passwords is sooooo much more interesting for an intruder and sooooo much more deadly.

> **BkkBonaza said:**
>  Kind of the opposite of a key logger.  I know. ;)

The only way I see this working is the way keyloggers work too. But then the keyboard would still need to be looped through that device.

Keyloggers sit between the keyboard and the PC and they record every keystroke that goes through. Now ... if you want to see the content you take the keylogger, you attach it to your own keyboard, you open an emtpy editor such as **"gedit"** (yes, no kidding!) and then you type the keylogger's magic password ..... and taaaadaaaaa ... ***Something*** starts typing inside your editor !!

It's the keylogger. It will look as if a ghost is typing in your previously empty editor window. The keyloggers I have experience with will show some kind of menu:

```
MAIN MENU (Memory 30% full)
1) Download keyboard log (detailed listing)
2) download Text log (show text only)
3) Erase log
4) change Password
5) disable Fast mode
6) Advanced download
7) Quit and return to operation
```

You type e.g. "1" into your "**gedit**" window and again the keylogger will start typing stuff into your empty window ... 

OP's device could work if it functioned like that. E.g. it is a keylogger and it scans for the strings "root" or "sudo" and then assumes that the next string that follows is the password. It then waits a few minutes, and only then injects the *payload* (= harmful code, or whatever ...).

Yes, *that* would work. But again ... why reinvent the wheel? Order one of those USB keyloggers and reverse-engineer it. Voila, done.

But have this USB "stick" sit in one port and then it injects code into the stream of the keyboard that sits in another port ...? Nope. I doubt it would work.
 

> **BkkBonaza said:**
>  Now that you clarified about using a laptop and not carrying a keyboard around it all doesn't sound as bizarre. Oh well, all in good fun. No problem ;)

---

### Post by Bjalf on 2009-11-28
> **scorp123 said:**
> And when I offered "to check if the network cable is loose" (= see if there is a keylogger on that PC he wants me to use) he all of a sudden insisted "Oh, no, don't go down there, too much dust and dirt. This PC works tip top. Just sit down and use it .... " 

I definitely didn't use it. I didn't trust this guy and that PC he wanted me to use not even one little bit.

Heh, I think I'd have grabbed the keyboard, "stumbled", and yanked it off "accidentally". No, really. I mean, if the sleazeball is **that** transparent ...  :p

Hmmm, in real life I'd probably have "checked" the cable anyway. Oooh, the opportunity to raise a monumentally big stink! "What is this?" "It's not yours?" "Must be mine then." Or just kick him in the nutz. "stumble" ... "sorry"


Could you use a one-time-password to check your mail? Would it be possible to set up a system where you carry a list of pre-generated use-once-and-discard gobbledegook passwords with you on paper (or cell phone), and use them to log on (somewhere) to check your mail? If you really need to be that careful (paranoid), you would not be safe from hidden spy cams in smoke detectors and so on.

---

### Post by scorp123 on 2009-11-28
> **Bjalf said:**
> Heh, I think I'd have grabbed the keyboard, "stumbled", and yanked it off "accidentally". No, really. I mean, if the sleazeball is **that** transparent ...  :p  Oh well :D

I just took my mobile phone and called our secretary ... done. :)

---

