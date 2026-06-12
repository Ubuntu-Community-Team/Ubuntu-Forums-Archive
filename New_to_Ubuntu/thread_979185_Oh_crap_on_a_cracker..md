---
title: "Oh crap on a cracker."
date: 2008-11-11
forum: New to Ubuntu
---

### Post by Obero on 2008-11-11
This is wierd. I have a Dell monitor, right? It's uh kind of new. Anyway, when I booted Ubuntu (for the first time) it got up just to the boot screen where I log-in but a message came up saying "Cannot display this video mode" or something along those lines. I reckon it's cause of Ubuntu's smaller resolution or something. How can I fix this? Anyway, this only happens to the actual operating system but when I boot the disc on "Try Ubuntu without saving anything" or whatever, it works. 

So, I tells ya, what's the problem?

---

### Post by Unanimated on 2008-11-11
Ohhhhhh, I gets this same issssuuueeeee.

Try hitting Ctrl+Alt+F1, and "sudo dpkg-reconfigure gdm."
I'm almost positive that won't work, but, you never know. If it doesn't, you could try "sudo dpkg-reconfigure xserver-xorg." I'm almost positive that won't work either, but it's a start.

---

### Post by ibuclaw on 2008-11-11
X screen config file might have gotten messed up in autoconfig.

Try booting into **recovery mode** in the GRUB boot menu and select the option **Fix X**.
Wait a few seconds for the job to complete and select the option the says **Continue with normal boot**

Tell us how that goes.

Regards
Iain

---

### Post by Obero on 2008-11-11
> **tinivole said:**
> X screen config file might have gotten messed up in autoconfig.

Try booting into **recovery mode** in the GRUB boot menu and select the option **Fix X**.
Wait a few seconds for the job to complete and select the option the says **Continue with normal boot**

Tell us how that goes.

Regards
Iain

Looks like this is an episode of House. Doc, the medicine you recommended had me go to the boot screen. I could see the cursor, I could see the log-in box. But wierd enough, it seemed like the mouse wasn't working. It was frozen. I couldn't even type with the keyboard. It was like all input devices were shutdown.

---

### Post by Obero on 2008-11-11
Don't leave me hanging, fellas.

---

### Post by Obero on 2008-11-12
Guys, it's been a day.

---

### Post by Tony Flury on 2008-11-12
If you really got to the recover log in - you would only need to use the keys, no mouse needed.

In GRUB you should have at least 3 Ubuntu options - your normal boot, recovery mode and memtest - make sure you choose Recovery mode just like tinivole said.

It does not even need a username password - you will just see a text screen with 4 options, use the arrow keys to scroll between them and use the return key to trigger that option.

The Fix X is the last option if I remember correctly

---

### Post by Obero on 2008-11-12
> **Tony Flury said:**
> If you really got to the recover log in - you would only need to use the keys, no mouse needed.

In GRUB you should have at least 3 Ubuntu options - your normal boot, recovery mode and memtest - make sure you choose Recovery mode just like tinivole said.

It does not even need a username password - you will just see a text screen with 4 options, use the arrow keys to scroll between them and use the return key to trigger that option.

The Fix X is the last option if I remember correctly

I did this, and I got to the log-in screen but the log-in screen is frozen.

---

### Post by Tony Flury on 2008-11-12
Did you get to the recovery mode at all ? or when you selected recovery mode did from GRUB did it just take you straight to the normal log-in.

Knowing what exactly happened might help me or others to help you.

---

### Post by Obero on 2008-11-12
> **Tony Flury said:**
> Did you get to the recovery mode at all ? or when you selected recovery mode did from GRUB did it just take you straight to the normal log-in.

Knowing what exactly happened might help me or others to help you.

I booted it, pressed 'ESC', then a list of "modes" came up. One of them was the recovery mode, so I clicked that, then another list of options came up, and 'Fix X' was one of them, so I clicked that, then after a bit of coding, it gave an option to use the regular mode and it got to the log-in screen (which is frozen.)

---

### Post by jamesrl on 2008-11-12
Can you get to a console login?  E.g. pressing [Ctrl]-[Alt]-F1 to get to a black/gray screen with login: ]

From there, have you tried either running 
```

sudo dpkg-reconfigure xorg-xserver

```

Also relevant: what is your video card [Intel/ATI/Nvidia + model], and what is your monitor.  I run ubuntu on a dual monitor setup (1920x1280 + 1680x1050) and it works fine, so I doubt it is a ubuntu can't handle large resolutions.  Its ubuntu by default isn't properly configured for your specific video card to correctly give output to your specific model.

---

### Post by Obero on 2008-11-12
> **jamesrl said:**
> Can you get to a console login?  E.g. pressing [Ctrl]-[Alt]-F1 to get to a black/gray screen with login: ]

From there, have you tried either running 
```

sudo dpkg-reconfigure xorg-xserver

```

Also relevant: what is your video card [Intel/ATI/Nvidia + model], and what is your monitor.  I run ubuntu on a dual monitor setup (1920x1280 + 1680x1050) and it works fine, so I doubt it is a ubuntu can't handle large resolutions.  Its ubuntu by default isn't properly configured for your specific video card to correctly give output to your specific model.

I'll try that, but to answer your questions, I'm not sure what my video card is. I only have a single Dell monitor.

---

### Post by Coreigh on 2008-11-12
Have you tried pressing the ctrl alt and + or ctrl alt and - Keys to rotate to a different resolution setting?

Boot the computer when you get that black screen with the error message press ctrl alt and - (minus key) all together. This will have X try the next lowest resolution setting. You might need to do it a couple times. If you get to a resolution you can see (even if it is not right) you can then go to the System >> Preferences >> Screen Resolution applet and set the correct resolution.

---

### Post by Obero on 2008-11-12
> **jamesrl said:**
> Can you get to a console login?  E.g. pressing [Ctrl]-[Alt]-F1 to get to a black/gray screen with login: ]

From there, have you tried either running 
```

sudo dpkg-reconfigure xorg-xserver

```

Also relevant: what is your video card [Intel/ATI/Nvidia + model], and what is your monitor.  I run ubuntu on a dual monitor setup (1920x1280 + 1680x1050) and it works fine, so I doubt it is a ubuntu can't handle large resolutions.  Its ubuntu by default isn't properly configured for your specific video card to correctly give output to your specific model.

So I tried the sudo thing, and it came up with "xorg-xserver not installed."

---

### Post by jamesrl on 2008-11-12
Sorry typo on my part.

it's xserver-xorg not xorg-xserver.

---

