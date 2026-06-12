---
title: "Am I using Gnome?"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by mirkaim on 2011-09-27
This is probably such a noob question but I have to ask. How do I know if I am using Gnome? I am trying to get themes and things and I know I'm using Unity but I don't know if that means I'm not using Gnome. 

From what I gather, Gnome and Unity are both shells but I could be wrong on that. Should I be asking this on a theme site instead? If so, which one would be good?

Thanks.

edit:
Can this be moved to the Desktop Environment forum?

---

### Post by mastablasta on 2011-09-27
Gnome is not a shell it's a desktop environment. Gnome shell is something else. Unity sits on top of gnome so to speak.
 
You GNOME themes probably don't work because you are using unity.

---

### Post by Alwimo on 2011-09-27
You wrote that you are using Unity, so you are using Gnome. Unity is Gnome plus a bit more. :)
 
Themes that work with Gnome should work with Unity but they'll look different because of that little bit more that Unity adds. Like if you maximise a window, the theming of the top part of the window will disappear in Unity as it blends with the top panel. In Gnome without Unity, it doesn't blend with the top panel.

---

### Post by mirkaim on 2011-09-27
I think I see. In Ubuntu I can see that Unity is Gnome but has that bar and changes the interface. At the login screen, I can see different modes like Ubuntu and Ubuntu Classic. Ubuntu loads Unity, I believe and Classic loads Gnome, right?

But in Linux Mint 11, the login screen shows options for Gnome and Gnome (No Effects). Is this the same, meaning that Gnome is Unity and Gnome (No Effects) is just Gnome like Ubuntu Classic?

---

### Post by mcduck on 2011-09-27
> **mirkaim said:**
> I think I see. In Ubuntu I can see that Unity is Gnome but has that bar and changes the interface. At the login screen, I can see different modes like Ubuntu and Ubuntu Classic. Ubuntu loads Unity, I believe and Classic loads Gnome, right?

But in Linux Mint 11, the login screen shows options for Gnome and Gnome (No Effects). Is this the same, meaning that Gnome is Unity and Gnome (No Effects) is just Gnome like Ubuntu Classic?

Whichever option you choose, you'll be using Gnome.

"Ubuntu" loads Gnome with Compiz and Unity
"Ubuntu Classic" loads Gnome with Compiz
"Ubuntu Classic (No effects)" loads just Gnome

What comes to themes, it makes no difference which session you use, what themes you need depends simply on which toolkit your programs are using. So you'll be looking for GTK2 themes to change how your applications look like, and Metacity themes to change the window borders.

---

### Post by mastablasta on 2011-09-27
+mint doesn't have the unity interface. i am not sure how they will proceed sicne there actually wont' be any more gnome classic interface. 
 
there is talk abotu gnome fallback mode but even that will probably go away eventually. and Gnome3 has it's Gnome shell (or in case of Ubuntu it will have Unity)

---

### Post by grahammechanical on 2011-09-27
Right now I am using the development release of Ubuntu 11.10. When I open System Settings and load the system Info utility I find out that I am running Gnome version 3.1.92. But I am also using the Unity desktop environment/interface.

At present there are only four themes available. More might be made available by the time 11.10 becomes a distribution release in November. It all depends on people developing themes that work with Gnome 3 and Unity 3d and the Unity 2D fall back mode for computers that do not have the hardware to run enhanced graphic effects.

As my father would say: "It is as clear as mud."

Regards.

---

### Post by mastablasta on 2011-09-27
Unity is not a desktop enviroment. it's a user interface for GNOME

---

### Post by technosysind on 2011-09-27
U can install sysinfo from ubuntu software center and check exactly what you are using. It will solve all your problems.

---

### Post by haqking on 2011-09-27
just type:

```
echo $DESKTOP_SESSION
```

from terminal

---

