---
title: "[SOLVED] Open folder from panel shortcut"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by ingeva on 2008-08-02
I have made a new "user" panel and want to store shortcuts from often used applications there. For some it's OK, for others I have trouble finding the solution.

For instance, I would like a quick open of some folders in nautilus file manager, but I seem to be unable to place nautilus there. The only way I can find is through the main menu and then I only come to the home folder etc.  Right-clicking from there just launches the application instead of presenting the "Add to Panel" option.

---

### Post by primolarry on 2008-08-02
You could create a launcher with the path as argument. Right click over the panel->add to panel -> create new launcher.

In the 'command' textbox, enter "nautilus desiredPath", for example

```
nautilus /media/main/documents
```

Regards

---

### Post by northern lights on 2008-08-02
In the new launcher's "command" input box, type ```
nautilus /path/to/folder
```where "/path/to/folder" needs to be replace by the actual path.

---

### Post by ingeva on 2008-08-02
> **northern lights said:**
> In the new launcher's "command" input box, type ```
nautilus /path/to/folder
```where "/path/to/folder" needs to be replace by the actual path.

I think I need a more detailed description. I have tried this, and when I click the icon I either get a message that the specified location is invalid, or nothing happens at all.

I have tried to define the application as "Application" and "Location". Same result.

**LAST: I eventually found what I was looking for:**

From nautilus I can drag an icon, for instance a folder, directly to the panel.
The properties will be as such (examples):

Name: examples
Location: file:///home/inge/Examples
Comment: Open '/home/inge/Examples'

---

### Post by northern lights on 2008-08-02
> **ingeva said:**
> From nautilus I can drag an icon, for instance a folder, directly to the panel
True. Should have rather told you that.
Nonetheless, given your example, ```
nautilus /home/inge/Examples
``` would have done it.

---

### Post by ingeva on 2008-08-03
> **northern lights said:**
> True. Should have rather told you that.
Nonetheless, given your example, ```
nautilus /home/inge/Examples
``` would have done it.

It did not. :)
file:///home/inge/Examples  did.

Thanks anyway. I learnt a lot from this.

It's what they say: It always helps to ask, and even if you don't always get the answer you're looking for you'll get some useful information.

You led me on the right track. By using "help" and searching the documentation I found the solution. If things  were that easy in Windows, I might still have been using it, but 20 years of daily frustration finally made me take time off for a week to get Ubuntu going! :)

(Now, after a week, I know I'll never return to Windows. It was like smoking: If I knew how easy it would be to quit, I would have stopped 10 years earlier!)

---

### Post by sayakb on 2008-08-03
Just drag n drop the folder/launcher to the panel.

---

### Post by ingeva on 2008-08-03
> **LinuxIsInnovation said:**
> Just drag n drop the folder/launcher to the panel.

Hmmm..... Wasn't that what I wrote in post #4? :)

The reason I had not tried that before (with folders) was that several other "things" couldn't be dragged into the panel. I though it wouldn't be possible.

I must be allowed to say that the menu and panel handling is clumsy with Gnome. It's actually one of the few places where Window is much better.

---

### Post by quinnten83 on 2008-08-03
> **ingeva said:**
> Hmmm..... Wasn't that what I wrote in post #4? :

People aren't always as up to date, he might have wrote his reply,while you writing yours. Or wasn't aware the answer was there already.

---

### Post by sayakb on 2008-08-03
Or maybe.. I just *did* miss out this one.. lol
Sorry for the redundant reply :)

---

### Post by ingeva on 2008-08-03
> **quinnten83 said:**
> People aren't always as up to date, he might have wrote his reply,while you writing yours. Or wasn't aware the answer was there already.

I know. That's why I usually scroll down to read the first posts of a thread if I read it for the first time.

No matter. This forum and people's willingness to help is very much appreciated. Couldn't do without it!

WOOOPS! Wrong quote. This was meant to be quoting LinuxIsInnovation / Sayak

---

### Post by ingeva on 2008-08-03
> **quinnten83 said:**
> People aren't always as up to date, he might have wrote his reply,while you writing yours. Or wasn't aware the answer was there already.

If you hadn't answered I wouldn't have seen your excellent articles about cusomizing Ubuntu. Thanks!

---

### Post by ingeva on 2008-08-03
> **ingeva said:**
> If you hadn't answered I wouldn't have seen your excellent articles about cusomizing Ubuntu. Thanks!

What's going on here?

I'm quoting the wrong post all the time! :)
This time I even edited the wrong one!   Is it me? :)

---

### Post by ingeva on 2008-08-03
> **ingeva said:**
> What's going on here?

I'm quoting the wrong post all the time! :)
This time I even edited the wrong one!   It it me? :)

Is there a way to remove your own posts so you can do it right?

---

### Post by sayakb on 2008-08-03
> **ingeva said:**
> If you hadn't answered I wouldn't have seen your excellent articles about cusomizing Ubuntu. Thanks!
Glad I could help!

> **ingeva said:**
> Is there a way to remove your own posts so you can do it right?
I don't think so, but you could always edit them and remove the quoted text.

Please mark the thread as solved. (Thread tools->Mark thread as solved)

---

### Post by ingeva on 2008-08-03
> **LinuxIsInnovation said:**
> Glad I could help!


I don't think so, but you could always edit them and remove the quoted text.

Please mark the thread as solved. (Thread tools->Mark thread as solved)

Thanks. Guess I was too much in a hurry! :)

---

### Post by northern lights on 2008-08-03
> **northern lights said:**
> In the new launcher's "command" input box, type ```
nautilus /path/to/folder
```where "/path/to/folder" needs to be replaced by the actual path.

> **ingeva said:**
> It did not [work]

Well, it does. There ain't no getting around it. Do you know that the shell is case-sensitive?

---

### Post by ingeva on 2008-08-03
> **northern lights said:**
> Well, it does. There ain't no getting around it. Do you know that the shell is case-sensitive?

SHELL?

We're not talking about shell here!

---

### Post by northern lights on 2008-08-03
> **ingeva said:**
> We're not talking about shell here!Absolutely we are. How do you think is the command that you type in the launcher processed?

The most generic meaning of the term shell is any program that users use to type commands. Desktop environments such as GNOME or KDE are by this definition nothing but graphical shells.

Anyhow, it is case-sensitive...

---

### Post by ingeva on 2008-08-03
> **northern lights said:**
> Absolutely we are. How do you think is the command that you type in the launcher processed?

The most generic meaning of the term shell is any program that users use to type commands. Desktop environments such as GNOME or KDE are by this definition nothing but graphical shells.

Anyhow, it is case-sensitive...

If you look at the title of the thread, you'll see that I was not asking for a shell command, but how to make a panel shortcut.

The problem is solved. Let's not argue.

---

### Post by northern lights on 2008-08-03
Never argued. Corrected a misunderstanding.

I figured you had an interest in your OS. If you prefer to remain in the wrong, it's your unalienable right.
:roll:

---

### Post by ingeva on 2008-08-03
> **northern lights said:**
> Never argued. Corrected a misunderstanding.

I figured you had an interest in your OS. If you prefer to remain in the wrong, it's your unalienable right.
:roll:

I admit you have more experience than I do,
but I have worked with Unix systems before,
so I know about terminal, and I know about shells.

I have no problem running terminal, and I have no problem using a shell,
but that was not what the question was about.

The misunderstanding is yours, completely. Sorry.

---

### Post by ingeva on 2008-08-03
> **ingeva said:**
> The misunderstanding is yours, completely. Sorry.

Sorry again.

I did exactly the same as I had done several times before, but this time it worked just as you said. Strange.

Oh, well. Sometimes it helps to be stubborn. :)

---

### Post by northern lights on 2008-08-03
> **ingeva said:**
> I admit you have more experience than I doThat might not even be true.

You simply had you're definition of the term "shell" not exactly right.

And as an aside, I suppose you had previously typed "examples" instead of "Examples", which makes a difference.

Thank you for having balls and admitting to a mistake. Courageous.

---

### Post by ingeva on 2008-08-03
> **northern lights said:**
> And as an aside, I suppose you had previously typed "examples" instead of "Examples", which makes a difference.

I can't say one or the other! :)

> **northern lights said:**
> Thank you for having balls and admitting to a mistake. Courageous.

Well I'm willing to admit to a mistake when I finally realize I made one! :)

I had tried what you suggested before and after your response and it failed every time. Why is a mystery to me because now it works every time! :)

I intend to stay here and ask questions and get answers. I'm also willing to help others (and soon I'll be able to!) but it's always smart to be a little humble! :)

---

