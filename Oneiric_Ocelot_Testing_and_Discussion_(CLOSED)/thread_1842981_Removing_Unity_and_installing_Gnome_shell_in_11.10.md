---
title: "Removing Unity and installing Gnome shell in 11.10?"
date: 2011-09-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by bpitsolutions on 2011-09-12
Is is possible for someone to strip out the Unity shell from Ubuntu 11.10 or 11.04 and install Gnome? I don't want to use the 'gnome classic' button in 11.04, and in 11.10 I'd like Gnome to be the default shell.  I've updated my desktop to 11.04 and 11.10 (separate ubuntu installs) and really dislike the Unity shell compared to the Gnome shell in Ubuntu 10.04 and 10.10.    I don't want to switch to Kubuntu as the KDE shell feels too similar to Microsoft Windows for my taste.  Is it as simple as an "apt-get remove" or an "complete remove" in the package manager....or is it more involved.  I'm willing to try if anyone has an answer.

Thank you in advance!

---

### Post by coffeecat on 2011-09-12
Since you've already updated to 11.10, I've moved your thread to the Oneiric testing forum where people experienced with Oneiric Beta will be able to answer your questions.

I'm a bit puzzled by your comments. You "don't want to use the 'gnome classic' button in 11.04" but "in 11.10 I'd like Gnome to be the default shell." By gnome I guess you mean the classic gnome panel desktop. If you install gnome-shell and gnome-session-fallback packages in 11.10, you'll get a classic gnome lookalike desktop with the gnome-session-fallback package which you will be able to select on login.

---

### Post by quarternote on 2011-09-12
Isn't Ubuntu 11.10 using Gnome 3 with gtk3, so it should be easy to install Gnome Shell.
You can choose from login screen if you want to use Unity or default Gnome which should be Gnome shell.
Ubuntu version 11.04 or earlier use Gnome 2 with gtk2, so there is bigger change to get something broken.
Someone who knows better could add some detail to this, but i hope this gives somekind of clue about your topic.

---

### Post by sammiev on 2011-09-12
That's all there is to it and you can switch from one to the other as easy as one click at log in. :)

---

### Post by bpitsolutions on 2011-09-12
Thank you all for your replies.  I did see the Gnome classic selection at the bootup screen.   I just dislike unity and would like to stick with gnome and ubuntu.  I'm not a power user yet and really am still a newbie when it comes to linux, but I do know that KDE is too much like Windows for me and Unity feels too much like Mac.  I'm happy with Gnome and it was a little disappointing to start playing with 10.04 and 10.10, getting used to Gnome and then when upgrading to 11.04 having Unity thrown at me.  I just didn't care for the look or feel of it as a new Linux user.

I guess if the Ubuntu folks were looking to attract new users with Unity, in my case I would say Unity is a bust.  I'll look into installing Gnome shell on 11.10.  That would also remove that Unity application launcher on the left side of the screen, correct?

---

### Post by coffeecat on 2011-09-12
> **bpitsolutions said:**
> I'll look into installing Gnome shell on 11.10.  That would also remove that Unity application launcher on the left side of the screen, correct?

If you install the packages I mention earlier, you'll get the choice of Unity 3d, Unity 2d, gnome shell and "classic" gnome at the login screen. If you select gnome shell or classic (I can't remember exactly what they are called in the login screen) you certainly won't get the Unity launcher. That's specific to Unity, but gnome shell does have its own launcher on the left.  If you don't like Unity you may not like gnome shell, or maybe you'll prefer it.

Another thing to consider. There are quite a number of people around the forum who took a dislike to Unity on first acquaintance (I'm one of them!) but have grown to prefer it. You never know.

Another alternative which some people prefer is the Xfce desktop in Xubuntu, which is certainly nothing like KDE.

---

### Post by rvchari on 2011-09-12
unity or gnome shell... i like them both as both are unique in their own way. i ve kept both as i like to switch as and when i am interested.

i installed shell through apt-get and everything seems to work fine.
i also installed gnome-tweak-tool...
i changed the icon theme and gtk3 themes through that but i am not able to get the shell theme changer or the shell extensions. i ve re-installed git and done all the exercise... but shell theme chooser / selector and extensions list does not show up...
is that bug due to the new version ? i also edited the metadata.jsaon with the current shell version still i am unable to get it...

another bug is the unity default top panel seems to show up in the back ground of the gnome-shell top panel... any chances to clear that ? as i said before, both are unique in their own style but when they cross over, it looks ugly ! any help will be appreciable.

i switched to beta1 purely because i wanted unity and gnome-shell to co exist in an un interuppted manner and let me choose the environment at login.

---

### Post by elvisd on 2011-09-20
Hi rvchari,

Hi have added ricotz repository to play with the latest gnome-shell version, and in synaptic i can install gnome-shell-extensions-common and ...-user-theme
Then in gnome-tweak-tool you can select the theme.

to add repository
```
sudo add-apt-repository ppa:ricotz/testing
```

I have the unity-panel in background to, have you found a solution to this?

---

### Post by elvisd on 2011-09-20
To resolve the panel issue remove, using synaptic, any *appmenu* app installed.

---

### Post by rvchari on 2011-09-20
ricotz ppa should not disturb existing unity... ? and do i have to remove existing gnome-shell and install gnome-shell from ricotz ?
finally when gnome 3.2 is released along with 11.10 stable, i ve got to re-do ? 

 i ll start this process !!!

the panel issue is a real pain in the neck ! if i remove the appmenu, i think unity will not have a global menu or will it function as it is ? let me try that too !

as i said earlier... the developers have done a wonderful job in gnome shell and unity and both are unique in their own respect...
it should be just fine to let the user choose at login !

---

