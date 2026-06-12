---
title: "[SOLVED] Firefox 3.0.4 - Bizarre Behavior"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by nomenclature3000 on 2008-11-19
Hi, Now that I've upgraded to Firefox 3.0.4, the forward and back buttons are permanently disabled, and the url never updates when I navigate to a new page. I've attached an image file in case you don't believe me, of this very web page! Bookmarks no longer work also.

Here are my FF details:

```

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.4) Gecko/2008111317 Ubuntu/8.04 (hardy) Firefox/3.0.4

```

Here is what I get in the shell when running firefox:

```

adam@tinkerbell:~$ firefox
GCJ PLUGIN: thread 0x805e918: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x805e918: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x805e918: NP_GetValue
GCJ PLUGIN: thread 0x805e918: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x805e918: NP_GetValue return
GCJ PLUGIN: thread 0x805e918: NP_GetValue
GCJ PLUGIN: thread 0x805e918: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x805e918: NP_GetValue return
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

```

Don't know if that's useful. I also reinstalled Firefox twice and restarted my machine. Please help! The browser is my lifeline!

---

### Post by philinux on 2008-11-19
Choose a different theme restart FF go back to your normal theme restart FF.

---

### Post by nomenclature3000 on 2008-11-19
Thanks for the suggestion. First I had to install a new theme, because I only had Default. I installed Abstract Classic, switched to it, restarted, switched back to Default, then restarted again. Nothing has changed. Any other suggestions?

---

### Post by nomenclature3000 on 2008-11-19
Does anyone know of a place where I can go to get paid help? Not being able to use my browser correctly is a significant hardship and is costing me. I would love to pay a tech support person to help.

Thanks,
Adam

---

### Post by kansasnoob on 2008-11-19
No idea about paid support, but do you use Thunderbird mail?

If so I CAN NOT help!

If the answer is no I believe I can help - for free!

---

### Post by nomenclature3000 on 2008-11-19
Thanks. I do not use Thunderbird mail.

---

### Post by kansasnoob on 2008-11-19
OK. I'm going to try and help. I'm going to go slow but if you don't understand something give me a shout!

I'm legally blind so it slows me down. Next post will include instructions.

---

### Post by kansasnoob on 2008-11-19
Go to Places > Home Folder. Click on View, then click on View Hidden. You'll see a folder named .mozilla

You see that?

I also need to ask you if you have anything saved in Firefox besides bookmarks that you want or need to save:confused:

---

### Post by nomenclature3000 on 2008-11-19
Hi, Thanks very much for your help so far. I grabbed a backup of my bookmarks out of ~/.mozilla before I made my first post. There is no other data I need in this folder, as far as I know.

---

### Post by kansasnoob on 2008-11-19
Well, just to be on the safe side, assuming you've found .mozilla, just right click .mozilla and select copy.

Then in the "Places" column select Desktop and then right click and select "paste". That way we have a backup of your .mozilla so if we want to revert we can easily do so.

Neat huh!

Now, since you mentioned an earlier backup I wonder if you might have made that backup while Firefox was still open? If so that might be your problem.

Anyway we can always restore what's needed.

If you only want to save bookmarks double click .mozilla, then double click Firefox, then double click "8random#".default!

Now, I use 8random#.default - but the 8 random figures will always be different! I used to jokingly call it ipfreely.default but some folks found that disgusting! Oops!

Anyway double click 8random#.default and then right click places.sqlite and select copy then save them to desktop just like we did the whole .mozilla! places.sqlite is your bookmarks!

Are we on the same page so far?

---

### Post by nomenclature3000 on 2008-11-19
Hi, I really appreciate the help. I should mention that I've been using Ubuntu for over a year and also regularly deploy my sites on CentOS servers, so I'm quite accustomed to working with the Linux filesystem from the shell. At any rate, as I said in my last post, I backed up everything from this folder that I need prior to making my initial post. Once again, I really appreciate your help, but if you would like to simply state the solution you have in mind, you might save yourself some time.

---

### Post by nomenclature3000 on 2008-11-19
Thanks very much again for your help. I divined where you were going and blew away my ~/.mozilla folder. Firefox now works correctly, and I was able to reinstate my bookmarks using the backup. Problem solved! I will click the "Thank you" button. Really appreciate it.

---

### Post by kansasnoob on 2008-11-19
If you've understood so far the next step is to click the "up" arrow in the file browser until you get back to .mozilla and then right click .mozilla and select "move to trash"!

Yeah! We're tossing it! That's why we needed to back things up in a manner where they could easily be found! I'll grant you it's overkill but I hate losing my stuff!

The next step is very simple. You must restart Firefox by clicking File > Quit and then opening Firefox again!

---

### Post by kansasnoob on 2008-11-19
> **nomenclature3000 said:**
> Thanks very much again for your help. I divined where you were going and blew away my ~/.mozilla folder. Firefox now works correctly, and I was able to reinstate my bookmarks using the backup. Problem solved! I will click the "Thank you" button. Really appreciate it.

Awesome! Been there and done this! Glad I could help and thank you back for your patience! That's what I love the most about Ubuntu!

The people!

---

### Post by kansasnoob on 2008-11-19
> **nomenclature3000 said:**
> Hi, I really appreciate the help. I should mention that I've been using Ubuntu for over a year and also regularly deploy my sites on CentOS servers, so I'm quite accustomed to working with the Linux filesystem from the shell. At any rate, as I said in my last post, I backed up everything from this folder that I need prior to making my initial post. Once again, I really appreciate your help, but if you would like to simply state the solution you have in mind, you might save yourself some time.

Just so those NOT disability challenged might understand:

Those of us with disabilities MUST do everything in consistent steps! I was not always disabled so I do understand how this is redundant and annoying to others.

For some of us it's not as simple as one foot in front of the other!

---

