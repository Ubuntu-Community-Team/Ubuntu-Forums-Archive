---
title: "thunderbird 31.0 - unable to enter header data"
date: 2014-07-25
forum: New to Ubuntu
---

### Post by tamas3 on 2014-07-25
Greetings,

Thunderbird 31.0 has just installed itself on my Ubunt 12.04.
Since this time I cannot access the data in the header when writing a new message or willing to reply to an incoming message. 

So, no way to add:
- sender
- to
- subject.

What can I do to make it work?

Thanks,

Tamás

p.s.
It used to work fine before this version...

---

### Post by amanchesterman on 2014-07-25
Personally I would be inclined to remove Thunderbird and reinstall. I have Xubuntu rather than Ubuntu, but in principle the steps are:
1) Find your existing TBird profile folder. It should be at something like /home/(username)/.thunderbird. Note the dot '.' before 'thunderbird'. That makes it a hidden folder, so if you look for it in your file manager you may not see it. You need to find the setting to 'show hidden files'.
2) Inside the folder there should be a folder named 'xxxxxxxx.default', where 'xxxxxxxx' is an arbitrary string of letters and numbers. This folder contains all your saved emails, email settings etc. **Make a safe backup copy of it before you do anything else**. (you can simply copy it to another folder, or rename it 'xxxxxxxx.old' or something like that.)
3) Using Synaptic Package Manager, remove Thunderbird. Select the 'completely remove' option.
4) Restart your machine.
5) Reinstall Thunderbird from the Software Center.
6) Locate the new Thunderbird profile. It will be in the same location as the previous one, but will have a different string of letters and numbers as the name 'xxxxxxxx.default'.
7) Copy your old Thunderbird profile to that location, and **rename** it to give it the **new** name that has just been created by the new installation.
8) Start Thunderbird. You should find all your saved emails, email accounts etc., as they were before, but with a completely fresh installation of the program itself.

---

### Post by Gordonbp531 on 2014-07-26
> **tamas3 said:**
> Greetings,

Since this time I cannot access the data in the header when writing a new message or willing to reply to an incoming message. 

So, no way to add:
- sender
- to
- subject.



Not sure what you mean by not able to add "sender" - the Sender gets inserted automatically depending on what email account you're in.
Can you post a screenshot of your New Mail window?
(31.0 works perfectly OK here on 14.04.1...)

---

### Post by tamas3 on 2014-07-26
Thanks, Gendibal, for your message. 

Please, find attached a snapshot. The header of the reply-message is dimmed. 
The subject is filled out automaticaly, however, the **To** field is left empty and I cannot write into it. 

I have several e-mail accounts. The **From** is dimmed now, as well. 
I used to be able to change to another sender account by clicking on the right side of the field, and selecting from my existing accounts. 
Now it is unchangeble... 

All this only since the new 31.0 version...

Friendly greetings,

Tamas

---

### Post by tamas3 on 2014-07-26
Thanks, [**[COLOR=#000000]amanchesterman[/COLOR]**]("http://ubuntuforums.org/member.php?u=904255")! Your step-by-step instructions are very clear! I could follow them, I think, easily. 
You seem to be a good teacher! I appriciate it!

Well, if nothing else works... I would do that. 
However, if possible, I would be glad to found out WHAT caused this thing to happen?
And, may be, other people experience the same?

Greetings!

Tamas

---

### Post by tamas3 on 2014-07-29
Hi!
A new version (1.2.7) of ***Display Contact Photo plugin*** has been installed... and now **all works fine**, again. 
So, I guess, that it was the ***Display Contact Photo plugin*** what had caused the issue. 

Thanks,

Tamás

---

