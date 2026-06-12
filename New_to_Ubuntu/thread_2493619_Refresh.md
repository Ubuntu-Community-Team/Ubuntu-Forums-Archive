---
title: "Refresh"
date: 2023-12-20
forum: New to Ubuntu
---

### Post by mrpritam on 2023-12-20
Hi! I am Pritam. I'm new to Ubuntu. I installed Ubuntu on my pc yesterday. And it is running very smoothly. Now I want to know how I can refresh my desktop. Is there any button or commands to refresh desktop. Don't tell me to press F5. Because I already tried it. It doesn't actually work.

---

### Post by MAFoElffen on 2023-12-20
What exactly do you mean by "refresh your desktop"?

If you mean your Gnome Desktop get's locked up and your want to try to reset it without logging out...

<Alt><F2>,<r> does a refresh... If that does not work, then...

I had created a script "before" to do that using busctl... But I just retested it, and a recent change in Gnome broke that. LOL.

Do this instead.
```

killall -HUP gnome-shell
# OR
killall -HUP gdm3

```
Do <Cntrl><Alt<F4>, login, then try either of those two commands... Those two will kill the session and all open user app's, log you out, but not reboot the computer.

---

### Post by mrpritam on 2023-12-21
I want to refresh my ubuntu desktop like I used to do on windows 10 by clicking the right button of the mouse and on refresh button. Just a normal 'refresh'. And for your kind info my gnome desktop is neither locked nor hang.

---

### Post by MAFoElffen on 2023-12-21
I'll explain that in more "detail"... The hot-key sequence for that press and hold keys <Alts> and <F2>. That will bring up the run dialog box. Press the keys <r> then <Enter>, You will see a popup saying "Restarting". That will restart the session, without logging you off or closing the open applications. That is like repainting the screen.

If that does not work, then try to toggle to a Virtual TTY console screen, by simultainiously pressing the keys <Cntrl><Alt<F2>. That will get you to a console prompt in vtty2. Logging in with your credentials, do...
```

sudo killall -HUD gdm3

```
That will kill the locked-up desktop session and return you to the login screen.

---

### Post by mrpritam on 2023-12-22
Ok. Thanks for your time.

---

### Post by MAFoElffen on 2023-12-22
@mrpritam -- 
If this has answered your question, as I asked in your last thread, since you are fairly new I will explain. 

As members, when we start a thread in a support section, if we feel the thread is answered or resolved, then we mark our own threads as "Solved". You can do that by going to the first page of a thread, and use the "Thread Tools" link to mark that thread as Solved.

Doing so helps other users to find answers to their own questions about similar problems. It also helps other meber who are helping users, to identify Users that still need help, from those who already have been helped.

---

### Post by ActionParsnip on 2023-12-22
What does refresh on a Windows desktop actually do?

---

### Post by #&amp;thj^% on 2023-12-22
> **ActionParsnip said:**
> What does refresh on a Windows desktop actually do?

Almost off topic, but here is a pretty good explanation: [https://fossbytes.com/refresh-option-windows-actually-not-think/](https://fossbytes.com/refresh-option-windows-actually-not-think/)

---

### Post by ActionParsnip on 2023-12-22
> **1fallen said:**
> Almost off topic, but here is a pretty good explanation: [https://fossbytes.com/refresh-option-windows-actually-not-think/](https://fossbytes.com/refresh-option-windows-actually-not-think/)

It's not almost offtopic, if we know what refresh does in Windows then we may be able to replicate the functionality in Ubuntu and ask the posted question.

How is it "slightly offtopic" at all? Think about it...........

---

### Post by #&amp;thj^% on 2023-12-22
I gracefully withdraw the off topic suggestion, will edit my post.

---

### Post by MAFoElffen on 2023-12-22
*"Kids... You want me to turn this desktop around?"*  (LOL)

Sidenote teaching moment: ---> Some of us get a bit paranoid trying to stay within talking about Ubuntu & it's Flavor's related 'support topics', for their supported releases... <--- Some of us have been privately reminded of that. Sometimes publicly...

...Some of us have been whipped about from time to time for not staying within those boundaries here. Others seem to escape that, be naive to that, or just be oblivious to that. For the most part, I think we try to stay aware, polite, and within the guidelines here. If on the fringes, we try to bring that somewhere within it's reach... LOL

I see that time coming back again... With some specific members recommending repeatedly to use 'this' or 'that', which are outside of ()ubuntu and their recommended default applications and utilities(?). As Members, if we represent the support community for Ubuntu, we are held to certain things...

I'm also a Windows & Unix Admin... But am very careful what I share about those here, unless it directly relates to something Ubuntu Support related that the User is asking about.

[hr][/hr]
Meanwhile, back on the ranch... I think this is "Solved", just waiting for the OP to mark it as such.

---

