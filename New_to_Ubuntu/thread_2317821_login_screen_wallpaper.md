---
title: "login screen wallpaper"
date: 2016-03-20
forum: New to Ubuntu
---

### Post by flex567 on 2016-03-20
How can I prevent from my wallpaper becoming my login-screen wallpaper?

---

### Post by Dennis N on 2016-03-20
There is a dialog in XFCE at **Settings > Lightdm gtk+ greeter settings** that allows you to set the background on the greeter screen.

---

### Post by flex567 on 2016-03-20
I use stock ubuntu 15.10

---

### Post by yetimon_64 on 2016-03-20
> **flex567 said:**
> How can I prevent from my wallpaper becoming my login-screen wallpaper?

On 14.04 I stopped the system using my desktop image as a login screen wallpaper by changing the permissions of any image files to "640" from the usual "644". That is I set the access permissions for "others" to "no access" which stops the image being used as the login image.

See the attached screenshot for an example of an image that is set not to show in the login screen, the bottom permissions setting shows as "none". The stock "purple" background is used on the login screen if I select that image as my desktop. I have complete folders of images set with permissions like that one. That setting prevents lightdm even accessing the file let alone using it as the login screen image.

---

### Post by flex567 on 2016-03-20
I changed the permissions and the image still shows.

---

### Post by yetimon_64 on 2016-03-20
> **flex567 said:**
> I changed the permissions and the image still shows.

Did you log out fully or reboot with that image set with those permissions? I note here that even though I can't get the image to show on the login screen the image will still show with the lock screen only in use.

Edit: iirc, I had to restart lightdm fully with a reboot (alternatively you could use, "sudo service lightdm restart" in terminal) to get the changes to take.

---

### Post by flex567 on 2016-03-20
restarted my comp and the picture is stil there in the login screen.

---

### Post by yetimon_64 on 2016-03-20
It was a long while ago, and I remember doing the permissions; it may not have been the only change I made though sorry.

 Just came across a dconf setting I also may have changed at the time that may be worth a try, in terminal run the next command and see if it helps ...
```
 gsettings set com.canonical.unity-greeter draw-user-backgrounds false
``` then reboot or restart lightdm. Hope this is what I did at the time and helps a bit more :-) To reverse the changes if it doesn't help just run the same command in terminal with "true" at the end of the command instead of "false".

---

### Post by flex567 on 2016-03-20
still doesn't work

---

### Post by yetimon_64 on 2016-03-20
> **flex567 said:**
> still doesn't work

Ok, I'll let others put up some suggestions, that is all I can find I've changed at the moment and it works on 14.04 for me. 

Maybe if you install dconf-tools and try the "dconf-editor" command to have a look for any settings that may help with 15.10 while waiting for more replies. Good luck.

---

### Post by howefield on 2016-03-20
> **yetimon_64 said:**
> It was a long while ago, and I remember doing the permissions; it may not have been the only change I made though sorry.

Tested and working fine in stock 15.10 without the dconf change.

Another method is to change the login wallpaper to something else with the command

```
dbus-send --system --print-reply --dest=org.freedesktop.Accounts /org/freedesktop/Accounts/UserID org.freedesktop.Accounts.User.SetBackgroundFile string:pathtoyourwallpaper
```

Substitute "*ID*" with your ID, probably 1000 but you can check it with

```
id -u
```

and "*pathtoyourwallpaper*" with the actual path to the file you want to use.

---

### Post by flex567 on 2016-03-20
> On 14.04 I stopped the system using my desktop image as a login screen  wallpaper by changing the permissions of any image files to "640" from  the usual "644". That is I set the access permissions for "others" to  "no access" which stops the image being used as the login image.
This worked but in the beginning I set the permissions for the wrong picture.

---

### Post by yetimon_64 on 2016-03-20
> **flex567 said:**
> This worked but in the beginning I set the permissions for the wrong picture.
Good to hear, thought I'd missed something there for a bit. That is very easy to do in a folder full of pictures, so now I set all pictures that I store in ~/Pictures with those "640" permissions :).

Could you mark the thread as solved please? A link for how to do so if needed ... [[COLOR=#0000ff]--is here--[/COLOR]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") 
Regards, yeti.

Edit: thanks howefield for confirming the permissions worked for you :-).

---

### Post by flex567 on 2016-03-26
After the screen locks now I can see my wallpaper picture again in a lock-screen??

---

### Post by yetimon_64 on 2016-03-26
> **flex567 said:**
> After the screen locks now I can see my wallpaper picture again in a lock-screen??

Yes, the permissions technique does _*not*_ work on the lock screen. As I noted in post #6 ...
> I note here that even though I can't get the image to show on the log in  screen the image will still show with the lock screen only in use.

The devs sure make it hard to completely stop using your wallpaper, I have never found a way to stop that behaviour. I have only ever found how to stop the main log in screen displaying the wallpaper.

---

### Post by howefield on 2016-03-27
Try..

```
gsettings set com.canonical.unity-greeter draw-user-backgrounds false
```

```
gsettings set com.canonical.unity-greeter background 'path_to_picture'
```

Tested and working on 15.10 using a .jpeg file but I believe you can also use .png files.

---

### Post by flex567 on 2016-03-27
> gsettings set com.canonical.unity-greeter background 'path_to_picture'

Is this path_to_picture in quotes ?

---

### Post by howefield on 2016-03-27
> **flex567 said:**
> Is this path_to_picture in quotes ?

Keep the quote marks, change path_to_picture to whatever the actual path to your picture is.

For example, the actual command I used to test the lock screen was..

```
gsettings set com.canonical.unity-greeter background '/home/hugh/Pictures/sky.jpg'
```

---

### Post by flex567 on 2016-03-27
It seems that it works, although the lock screen is somewhat dark.

---

### Post by howefield on 2016-03-27
> **flex567 said:**
> It seems that it works, although the lock screen is somewhat dark.

Can't help you with that, not seeing that on this machine. Try a different picture maybe although I wouldn't think it is image specific ?

---

### Post by yetimon_64 on 2016-03-27
> **howefield said:**
> Try..

```
gsettings set com.canonical.unity-greeter draw-user-backgrounds false
```

```
gsettings set com.canonical.unity-greeter background 'path_to_picture'
```

Tested and working on 15.10 using a .jpeg file but I believe you can also use .png files.

Thanks howefield, Finally have no log in image and a custom lock screen (fixed image). Didn't think that was possible, works nicely here :-). Cheers, yeti

---

### Post by howefield on 2016-03-27
Cool, glad it helped you.

---

### Post by trilok2 on 2016-03-28
[COLOR=#111111][FONT=Ubuntu]Install dconf-editor either via the Ubuntu Software Center or CLI.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]In dconf-editor go to: com > canonical > unity > unity-greeter[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]and then make sure that the tick box draw-user-backgrounds is set to True.[/FONT][/COLOR]

---

### Post by yetimon_64 on 2016-03-28
> **trilok2 said:**
> [COLOR=#111111][FONT=Ubuntu]Install dconf-editor either via the Ubuntu Software Center or CLI.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]In dconf-editor go to: com > canonical > unity > unity-greeter[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]and then make sure that the tick box draw-user-backgrounds is set to True.[/FONT][/COLOR]
Wrong, the OP doesn't want the wallpaper to show in the lock screen. Doing what you suggest goes totally against what has already been shown to fix the OP's problems and will re-show the wallpaper even with a custom image set; note the thread is now marked as [SOLVED] by the OP.

See post 16 by Howefield for the correct setting for that dconf key for the OP's purposes ...
```
gsettings set com.canonical.unity-greeter draw-user-backgrounds false
```
... this is the identical setting you are saying to change via dconf-editor but as is altered from the terminal.

---

