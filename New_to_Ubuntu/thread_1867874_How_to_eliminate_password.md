---
title: "How to eliminate password"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by Mikhaill on 2011-10-23
Hello, What would be the command line to eliminate the need for passwords? I am the only user of my computer and I find it unnecessary to give authentication to make changes and to log in. Thanks.

---

### Post by Dry Lips on 2011-10-23
> If you disable the sudo password for your account, you will  seriously compromise the security of your computer. Anyone sitting at  your unattended, logged in account will have complete Root access, **and  remote exploits become much easier for malicious crackers**.Quote taken from:
[https://help.ubuntu.com/community/RootSudo#Remove_Password_Prompt_For_sudo](https://help.ubuntu.com/community/RootSudo#Remove_Password_Prompt_For_sudo)

---

### Post by sadaruwan12 on 2011-10-23
Welcome to the community!

Well, that decision is not a very good one the password prompt is there so the users get alerted when they do something to change the system like install application and run a command to update or to compile.

This prompt will give you chance to double check if you run a command harmful to your system you can cancel it from there with out running it. If you don't have it then even rough codes also can run and harm your system.

And I'm also a lone user no one else touches my PC or my Lap but I keep this 'cos it has saved me many a times so my advice to you is keep it it's good for you.

---

### Post by Mikhaill on 2011-10-23
> **Dry Lips said:**
> Quote taken from:
[https://help.ubuntu.com/community/RootSudo#Remove_Password_Prompt_For_sudo](https://help.ubuntu.com/community/RootSudo#Remove_Password_Prompt_For_sudo)

Thanks Dry Lips. I'm not sure I see the danger of disabling the password. This is a home computer. How would the risk be any greater than a computer running Windows OS? Should I install a specific security software? Thanks.

---

### Post by haqking on 2011-10-23
> **Mikhaill said:**
> Thanks Dry Lips. I'm not sure I see the danger of disabling the password. This is a home computer. How would the risk be any greater than a computer running Windows OS? Should I install a specific security software? Thanks.

The risk is that services, processes etc can now run as admin without authentication, browsing the net as root etc etc.

Blank or no passwords as not a best practice, and the physical access to a machine thing is of little consequence as physical access is root access anyways as it is easily obtained.

Read [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo")

The danger is everything you do will now be as admin (one of the issues with some setups of windows) as you meantioned it

---

### Post by critin on 2011-10-23
*<<How would the risk be any greater than a computer running Windows OS? Should I install a specific security software? Thanks.>>*

It probably wouldn't be any greater, but why take a risk at all?  Prowlers from the net/bad sites,  won't be able to install stuff, because they will need the password.  
I balked too at first.  No one touches my computer, but I kept it in and am very glad I did.  You get used to it--really.

I don't run any anti virus/spyware at all.  It's such a relief to not have to worry about it.  :)

It will also protect you from running a bad command.   What if you clicked delete by mistake?

---

### Post by nothingspecial on 2011-10-23
Think of it like this.

Your computer is a house.

Assuming your computer is connected to the internet then this house is in a city full of robbers, muggers, thieves, fraudsters etc etc

Your password is the key to the front door.

However annoying it might be to have to close your door and lock it, do you really want to go upstairs to bed, or go out with your door open and unlocked?

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-23
you have MUCH more control over your computer than a windows user.  So, keeping the sudo password sets up blocks so you don't do something without considering the implications.

But... some linux systems log you in as root.  puppy linux is a perfect example.
you can use a system as root and do fine, but it gives you more room for error especially when using a file manager, or terminal.  as root, you are not prompted with a password if you try to delete a needed file on accident.

---

### Post by kemtnbkr on 2011-10-23
I just have mine set to a really short 4-digit code for my main user profile, then I have a separate ssh profile set up with a much better password and no root access.  This minimizes my 'typing time' whenever I want to do something, and lets me stay *somewhat* secure.  I'm the only one that uses my desktop, btw.

I'd recommend doing that rather than just completely disabling the password.  Here's an example.  Say you want to completely delete a directory from the command line, and you have your always-root setup going.  So you start typing and accidentally hit enter before you finish.  You'll erase everything on your HD if you do that; if you leave the password on, you'll be able to cancel the command because you'll get the password prompt first.

I third the opinion of keeping your password enabled.

---

### Post by Dry Lips on 2011-10-23
> **Mikhaill said:**
> Thanks Dry Lips. I'm not sure I see the danger of disabling the password. This is a home computer. How would the risk be any greater than a computer running Windows OS? Should I install a specific security software? Thanks.

Check out what a "zombie" is:
[https://secure.wikimedia.org/wikipedia/en/wiki/Zombie_%28computer_science%29]("https://secure.wikimedia.org/wikipedia/en/wiki/Zombie_%28computer_science%29")

Windows computers with no password for administrative tasks, has resulted in such problems as 
described in the link above.

---

### Post by critin on 2011-10-23
You can choose not to use the password when logging in.  Change it in Users.

---

### Post by dFlyer on 2011-10-23
Here is the simple answer, ```
 dangerous commands
``` will delete your whole system without having to enter a password if your logged in as admin. The password is there to protect you from simple mistakes.

---

### Post by nothingspecial on 2011-10-23
Can we please refrain from posting commands that will destroy someone's system please.

Thank you.

---

### Post by Mikhaill on 2011-10-23
All very clear and very compelling reasons to keep my passwords. Thanks for your help.

---

