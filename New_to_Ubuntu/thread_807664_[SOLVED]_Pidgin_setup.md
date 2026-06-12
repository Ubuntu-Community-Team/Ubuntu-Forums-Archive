---
title: "[SOLVED] Pidgin setup"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by x88a on 2008-05-26
i am trying to setup a Pidgin account.
My email is [email]abc@gmail.com[/email]
i am using MSN.
what should i put in the Basic and Advanced section?
TQ

---

### Post by iaculallad on 2008-05-26
> **x88a said:**
> i am trying to setup a Pidgin account.
My email is [email]abc@gmail.com[/email]
i am using MSN.
what should i put in the Basic and Advanced section?
TQ

On the Basic if you're using gmail

Protocol: GoogleTalk
Screen Name: abc
Password: Your password for this google account

Check the remember checkbox if you're a single user to that computer or leave it uncheck if used by multiple users then click on save.

Leave the Advance tab untouched (Default settings)

---

### Post by dRock1286 on 2008-05-26
If you have your gmail account set up with MSN, then you can just use the MSN protocol as if you were using an MSN or Hotmail account...

---

### Post by x88a on 2008-05-26
> **dRock1286 said:**
> If you have your gmail account set up with MSN, then you can just use the MSN protocol as if you were using an MSN or Hotmail account...

yes, but the thing is, i cant connect.
What is "Screen Name"?
Where should i type my email address?
What should be typed in the advanced section?

TQ

---

### Post by iaculallad on 2008-05-26
> **x88a said:**
> yes, but the thing is, i cant connect.
What is "Screen Name"?
Where should i type my email address?
What should be typed in the advanced section?

TQ

Screen Name: 
> considering [email]abc@gmail.com[/email] as the sample email: You screen name should only be **abc**

Protocol: Choose** GoogleTalk**

Advance Section should contain:

> XMMP Options = All three check boxes should be uncheck.
Connect Port: 5222
Connect Server: talk.google.com
Proxy Type: Use GNOME Proxy Settings

---

### Post by x88a on 2008-05-26
are you sure i should be using Googletalk?
in Windows, i use MSN messenger with gmail email.
btw, i tried your method and it failed :(
pls help
tq

---

### Post by iaculallad on 2008-05-26
> **x88a said:**
> are you sure i should be using Googletalk?
in Windows, i use MSN messenger with gmail email.
btw, i tried your method and it failed :(
pls help
tq

Try using XMMP as protocol if it works for you.

---

### Post by victor.zamanian on 2008-05-26
Do not use GoogleTalk! I don't think these guys understand your question.

I just tested your situation out and the following worked for me:

Protocol: MSN
Screen name: [email]your-address-including@gmail.com[/email]
Password: whateveryourpasswordis
Local alias: Your "nickname"

I didn't even touch the advanced tab. Hope this helps. If you cannot connect, check your spelling on everything you typed in, and make sure that your account is still active in case you haven't been loggin in for quite a while.

Good luck!

---

### Post by sayakb on 2008-05-26
[iaculallad]("http://ubuntuforums.org/member.php?u=520984") is correct.
Screen-name: Your Gmail username (eg for [EMAIL="abc@gmail.com"]abc@gmail.com[/EMAIL], type abc)
Protocol: Google Talk
And just enter your password.

EDIT: You might leave the Alias blank, depending on if or not you want to show up your nickname.

---

### Post by x88a on 2008-05-26
got it
thanks a lot

---

### Post by iaculallad on 2008-05-26
> **x88a said:**
> got it
thanks a lot

That was just what Im telling you but it seems that you're not reading it well. Next time, when you ask a question and somebody answers it for your, perform it for yourself first and be very observant.

> XMMP Options = All three check boxes should be uncheck.
Connect Port: 5222
Connect Server: talk.google.com
Proxy Type: Use GNOME Proxy Settings

The settings above are just the default for Pidgin, and I assume that you touched and made changes on it so I posted it for you to copy. Anyway, goodluck on using your newly configured Pidgin App.

---

### Post by x88a on 2008-05-27
> **iaculallad said:**
> That was just what Im telling you but it seems that you're not reading it well. Next time, when you ask a question and somebody answers it for your, perform it for yourself first and be very observant.



The settings above are just the default for Pidgin, and I assume that you touched and made changes on it so I posted it for you to copy. Anyway, goodluck on using your newly configured Pidgin App.

u cant use googletalk.
have to use MSN

---

### Post by victor.zamanian on 2008-05-27
> **x88a said:**
> got it
thanks a lot

If you acquired the solution to your problem, it's good if you go to "Thread tools" and select to mark this thread as "[SOLVED]". Also perhaps post on which one of all the replies you got was helpful to you.


Thanks for being a part of the forum, and good luck!

Victor

---

