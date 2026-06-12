---
title: "Gnome-shell 3.2 released"
date: 2011-09-27
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-09-27
The new release of Gnome-shell (3.2) is now available from Ricotz Testing PPA along with mutter 3.2 and gobject-introspection 1.30.

They are looking good.

---

### Post by sgage on 2011-09-27
> **Harry33 said:**
> The new release of Gnome-shell (3.2) is now available from Ricotz Testing PPA along with mutter 3.2 and gobject-introspection 1.30.

They are looking good.

Looking good here! I guess tomorrow is the official Gnome 3.2 release date. I am very happy with GS.

---

### Post by sonnet on 2011-09-27
I updated and everything went fine. No noticeable change other than system-settings -> appearence now works.

Although I'm bit disappointed by memory usage:
330mb with mutter and 280mb with gnome classic session (looking with gnome system monitor).

I have installed a minimal ubuntu server and then installed gnome-shell over it.

Reason I'm disappointed is that I have seen people with Gnome 3 having an usage of just 120mb.
Now, I know Ubuntu usually use more memory than other distros, but with Gnome 2, I used to build the same minimal installs with both Debian and Ubuntu and get an usage of 130mb with Debian and 160 with Ubuntu.
So I was expecting here an usage of 160 or anyway below 200mb.

Do you think it's Ricotz packages or I'd have to expect the same with official Ubuntu packages?

---

### Post by jbicha on 2011-09-27
Ricotz's packages are virtually the same as the official ones. He's part of the Desktop Team.

Your memory use might be because of your graphics driver.

---

### Post by makitso on 2011-09-27
Harry,  thanks for keeping us updated!

---

### Post by tekstr1der on 2011-09-27
> **sonnet said:**
> I updated and everything went fine. No noticeable change other than system-settings -> appearence now works.

Although I'm bit disappointed by memory usage:
330mb with mutter and 280mb with gnome classic session (looking with gnome system monitor).


Holy smokes! Is this a radical change from your experience with gnome 3.0.x? I am using gnome-shell on Arch and it sits idle at 97MB. Are you sure you're not counting buffers/cache in your figures?

---

### Post by cariboo on 2011-09-27
> **sonnet said:**
> I updated and everything went fine. No noticeable change other than system-settings -> appearence now works.

Although I'm bit disappointed by memory usage:
330mb with mutter and 280mb with gnome classic session (looking with gnome system monitor).

I have installed a minimal ubuntu server and then installed gnome-shell over it.

Reason I'm disappointed is that I have seen people with Gnome 3 having an usage of just 120mb.
Now, I know Ubuntu usually use more memory than other distros, but with Gnome 2, I used to build the same minimal installs with both Debian and Ubuntu and get an usage of 130mb with Debian and 160 with Ubuntu.
So I was expecting here an usage of 160 or anyway below 200mb.

Do you think it's Ricotz packages or I'd have to expect the same with official Ubuntu packages?

What difference does it make how much ram your system is using, as long as you aren't running into the swap partition regularly? This obsession with ram usage is a leftover from using Windows XP, Vista and Windows 7 use ram the same way Linux does. Programs are cached so that they load faster. Remember unused ram is wasted ram. :)

---

### Post by sonnet on 2011-09-28
> **jbicha said:**
> Ricotz's packages are virtually the same as the official ones. He's part of the Desktop Team.

Your memory use might be because of your graphics driver.

No it can't be, as far as I have seen, installing the Nvidia proprietary driver didn't increase my memory usage neither with gnome 2 or Kde 4. I some case I noticed even a slight reduction than when using Nouveau driver.

> **tekstr1der said:**
> Holy smokes! Is this a radical change from your experience with gnome 3.0.x? I am using gnome-shell on Arch and it sits idle at 97MB. Are you sure you're not counting buffers/cache in your figures?

I had the same doubt. I thought that maybe it was something changed in gnome-system-monitor, so I run free -m command, and I got similar results (total 600mb of ram used, 300mb of which is buffers/cache)

> **cariboo907 said:**
> What difference does it make how much ram your system is using, as long as you aren't running into the swap partition regularly? This obsession with ram usage is a leftover from using Windows XP, Vista and Windows 7 use ram the same way Linux does. Programs are cached so that they load faster. Remember unused ram is wasted ram. :)
You are right. But if it was just Gnome I wouldn't be too much worried. What worries me is why Ubuntu setup makes use of much more ram than other distros? As I said I never found big difference with minimal Ubuntu installs compared to other distro like Debian. Usually the difference was about 30 mb ,which I find negligible.
But this time is 3 times what it should be.
So I wondered if this extra memory is really well used, or is a bug/wrong way to package.

---

### Post by syedyaqubali on 2011-09-28
Hi I am new to ubuntu i have installed gnome also .But when i try login with gnome as console at login menu it gives error as "gnome-fallout".Please reply me how to over come this problem.

---

### Post by syedyaqubali on 2011-09-28
Hi I am new to ubuntu i have installed gnome also .But when i try login  with gnome as console at login menu it gives error as  "gnome-fallout".Please reply me how to over come this problem.And also my system is getting slow also.

---

### Post by Mystro256 on 2011-09-28
> **tekstr1der said:**
> Holy smokes! Is this a radical change from your experience with gnome 3.0.x? I am using gnome-shell on Arch and it sits idle at 97MB. Are you sure you're not counting buffers/cache in your figures?

It's a Ubuntu thing, I noticed when I switched over to Arch myself. Ubuntu most have a lot of random stuff running by default lol


> **sonnet said:**
> I updated and everything went fine. No noticeable change other than system-settings -> appearence now works.

Although I'm bit disappointed by memory usage:
330mb with mutter and 280mb with gnome classic session (looking with gnome system monitor).

I have installed a minimal ubuntu server and then installed gnome-shell over it.

Reason I'm disappointed is that I have seen people with Gnome 3 having an usage of just 120mb.
Now, I know Ubuntu usually use more memory than other distros, but with Gnome 2, I used to build the same minimal installs with both Debian and Ubuntu and get an usage of 130mb with Debian and 160 with Ubuntu.
So I was expecting here an usage of 160 or anyway below 200mb.

Do you think it's Ricotz packages or I'd have to expect the same with official Ubuntu packages?

I would suggest XFCE (Xubuntu) if you're having ram issues, especially because it's very similar to classic gnome.

---

### Post by sonnet on 2011-09-28
> **Mystro256 said:**
> It's a Ubuntu thing, I noticed when I switched over to Arch myself. Ubuntu most have a lot of random stuff running by default lol




I would suggest XFCE (Xubuntu) if you're having ram issues, especially because it's very similar to classic gnome.

I know I can use XFCE, but I want to use Gnome. It's not a real issue ,as I have enough memory , I just wanted to know why such unexplainable huge difference between Ubuntu and the other distros

---

### Post by tekstr1der on 2011-09-28
> **cariboo907 said:**
> What difference does it make how much ram your system is using, as long as you aren't running into the swap partition regularly? This obsession with ram usage is a leftover from using Windows XP, Vista and Windows 7 use ram the same way Linux does. Programs are cached so that they load faster. Remember unused ram is wasted ram. :)

Cariboo: While you are correct in that linux and Win7/Vista similarly attempt to cache as much memory as possible to improve responsiveness (and this is a very good thing), the OP has raised a very legitimate concern. The same DE, even on different distros, should not vary in its commit load-out by a factor of 3x. This is highly suspect.

If every application were to be designed such that it used as much ram as the developer *desired* (2GB x86 process limit for example), and there were no longer any concerns for memory economy, you'd be in swap madness constantly after starting more than one program.

---

### Post by jbicha on 2011-09-28
Ubuntu ships the same GNOME Shell as upstream. Except for a few FTBFS patches, we patch GNOME Shell to show Ubuntu's preferred apps as favorites (Fedora 16 does this also) and we patch Mutter so that Ambiance/Radiance displays ok.

To be fair, you do know that Arch and Debian experimental currently ship GNOME 3.0, not 3.2, right?

---

### Post by morgenstond on 2011-09-28
Anyone else have a problem with dual monitor setup? The second screen (to the right) has a white edge at the top, on which right clicking doesn't work. 

Could this be caused by Unity or is it a gnome-shell bug?

I'm on the nvidia binary. Not sure if nouveau has the same problem.

---

### Post by alexvy13 on 2011-09-28
I tried it again for about the third time, liked the UI but decided to switch back to unity : ) but, the adwaita theme is still in my settings, and I no longer have a networking option in system settings. I have tried apt-get purge gnome shell and autoremove several times and bleachbit and gtkorphan. I'm pretty sure I have removed all supposedly traces of gnome shell 3.2 but I still would like the adwaita theme gone and my networking options back.

---

### Post by jbicha on 2011-09-29
alexvy, remove gnome-themes-standard to kill Adwaita. I don't know what you removed to mess up your networking. Do you have network-manager-gnome installed?

---

