---
title: "Can I change keyboard keys?"
date: 2012-08-05
forum: New to Ubuntu
---

### Post by MibunoOokami on 2012-08-05
Hi all,

I'll try keep this short for everyone. I use a non English layout for my netbook's keyboard, as it happens, my netbook has less keys than a full sized keyboard and as a result, I'm left without an underscore key, but I do have 2x tilde (~) keys and if it's possible I would like to make one into an underscore key.
Could someone please tell me if this is possible and if so, could you walk me through the process too please? Thank you.

---

### Post by GreatDanton on 2012-08-05
System settings>Keyboard layout>Options. There are several options for changing keys, however I am not sure if there is an option for your problem.

Regards.

---

### Post by MibunoOokami on 2012-08-06
> **GreatDanton said:**
> System settings>Keyboard layout>Options. There are several options for changing keys, however I am not sure if there is an option for your problem.

Regards.

Hi, thanks for your reply. I've just spent some extra time checking out the layout options, but I can't see anything that allows me to change the input/output of a key.

---

### Post by GreatDanton on 2012-08-06
Okay since previous option didn't solve your problem, then try this : [http://askubuntu.com/questions/24916/how-do-i-remap-certain-keys](http://askubuntu.com/questions/24916/how-do-i-remap-certain-keys)

Regards.

---

### Post by MibunoOokami on 2012-08-07
> **GreatDanton said:**
> Okay since previous option didn't solve your problem, then try this : [http://askubuntu.com/questions/24916/how-do-i-remap-certain-keys](http://askubuntu.com/questions/24916/how-do-i-remap-certain-keys)

Regards.

Hi, thanks for that, I didn't realise it's called mapping. Before I attempt to remap one of my keys, I just want to verify that I understand the process correctly.

The key I want to change has the following ID > state 0x1, keycode 21 (keysym 0x7e, asciitilde), same_screen YES, That's using the shift key at the same time.
Since technically I'm trying to add a key stroke which doesn't currently exist, will I need to also change the XLookuoString line too?
I'm not 100% on the keycode I should actually use. In the third line as per those instructions, it's identified as key 21, but the fourth line identifies it as key 19.
I know it says only worry about the third line, but I just want to be extra cautious.
> XKeysymToKeycode returns keycode: 19Should my code should look like this?
 ```
xmodmap -e "keycode 21 = asciicircum asciiunderscore"
```

I assume the current mapping of the key is "asciicircum asciitilde" so I'm just changing the tilde to underscore.
Thanks

---

### Post by GreatDanton on 2012-08-07
> Note that if the key you are mapping should have a different meaning  when used with the shift key (for example for British keyboard layouts, Shift+2  gives quotation marks) then you can simply list the secondary command  after the first. For example if you want the key with code 53 to map to  backslash normally, but to the bar symbol when used with shift, you  might do:
   xmodmap -e "keycode 53 = backslash bar" 

Just follow the instructions. I can't tell you for sure, since I have never done something like that (Us/Slo keyboard). Follow the instructions and don't be afraid to try something. Like it's said > **Note: These change are for the active x session only and will be lost after reboot. When you want to save the changes permanently you have to run the following commands after the ones above:**

all changes will be lost after reboot, so you can't do nothing wrong. For example if you made something and then realize that was not what you wanted to do, just reboot and the changes will be lost. However when you change the right thing go ahead and make permanent change.

Good luck!

---

### Post by MibunoOokami on 2012-08-07
> **GreatDanton said:**
> 
all changes will be lost after reboot, so you can't do nothing wrong. For example if you made something and then realize that was not what you wanted to do, just reboot and the changes will be lost. However when you change the right thing go ahead and make permanent change.

Good luck!

Thanks, that's a good point that I didn't think about. I was too busy over analysing things.

I've given it a go and got this message.
> xmodmap -e "keycode 21 = asciicircum asciiunderscore"
xmodmap:  commandline:1:  bad keysym name 'asciiunderscore' in keysym list
xmodmap:  1 error encountered, aborting.

---

### Post by GreatDanton on 2012-08-07
It seems that's not the right name for the underscore key. Check this page;
[http://wiki.linuxquestions.org/wiki/List_of_Keysyms_Recognised_by_Xmodmap](http://wiki.linuxquestions.org/wiki/List_of_Keysyms_Recognised_by_Xmodmap)

It looks like keysim code for underscore is     0x05f. Try to put this instead of asciiunderscore.


P.S I am just guessing, but it cost you nothing to try out.

Regards.

---

### Post by MibunoOokami on 2012-08-07
> **GreatDanton said:**
> It seems that's not the right name for the underscore key. Check this page;
[http://wiki.linuxquestions.org/wiki/List_of_Keysyms_Recognised_by_Xmodmap](http://wiki.linuxquestions.org/wiki/List_of_Keysyms_Recognised_by_Xmodmap)

It looks like keysim code for underscore is     0x05f. Try to put this instead of asciiunderscore.


P.S I am just guessing, but it cost you nothing to try out.

Regards.

Thanks for your patience and help GreatDanton, that did the trick and I've now followed the necessary steps to save the change. I can't reboot to see if I saved it properly until later today, but when I do, I'll post to let you know.
Thanks again.

---

### Post by GreatDanton on 2012-08-07
You are welcome. I would also like to thank you, because I also learned a lesson today. I didn't know how to do it before :oops:.

After reboot; if everything is okay please mark thread as solved (Thread tools>mark thread as solved).

Regards.

---

### Post by MibunoOokami on 2012-08-08
> **GreatDanton said:**
> You are welcome. I would also like to thank you, because I also learned a lesson today. I didn't know how to do it before :oops:.

After reboot; if everything is okay please mark thread as solved (Thread tools>mark thread as solved).

Regards.

You're welcome too. Reboot was successful and I now have an underscore key which is what I wanted. Thanks again.

---

