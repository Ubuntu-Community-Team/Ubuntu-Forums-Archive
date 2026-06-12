---
title: "Facebook on Chromium"
date: 2013-07-07
forum: New to Ubuntu
---

### Post by 3dmatrix on 2013-07-07
I am facing a strange problem since some days.
On one of the partitions with Ubuntu 13.04 (with all updates done), the chromium browser is presenting a strange problem.
I can access Facebook through every other browser but not through Chromium.
I purged it in apt, deleted .config and .cache files of chromium, deleted the deb files in apt archive but still when i reinstall it, it does not works. It can access every other website but not Facebook. After installing, when i type facebook, then the auto complete in the address bar shows a lot of other facebook sites that i visited earlier, that means still some files are present in the system that has the old data. Can anyone advise what could be going wrong ?

.

---

### Post by Feathers McGraw on 2013-07-07
Did you log in to chromium?

Google syncs your history, bookmarks etc. across browsers if you let it, that could be why facebook appears in your history.

As to why you can't access facebook... not a clue, sorry!

Feathers

---

### Post by 3dmatrix on 2013-07-07
I never log in Chromium.

---

### Post by Feathers McGraw on 2013-07-07
Well that shot my theory out of the water :p

---

### Post by 3dmatrix on 2013-07-07
Apart from  .config and .cache folders where else can chromium's files be located so that i could manually delete them b4 reinstalling it.

---

### Post by 3dmatrix on 2013-07-10
Any help or suggestion ?

---

### Post by VinDSL on 2013-07-10
```
chrome://version/
```
...should show your profile path.  ;)

---

### Post by 3dmatrix on 2013-07-10
So you mean it was my profile that was creating trouble ?

---

### Post by VinDSL on 2013-07-10
> **3dmatrix said:**
> So you mean it was my profile that was creating trouble ?
Hard to say.  I just mentioned that URI because it shows the paths to various things, including your profile.

I'm running two Chromium installs (Chromium 27/stable & Chromium 30/untested/unstable trunk build)

I keep the two profiles separate from one another.

Sometimes, just creating a new profile, by designating a new path in the command line, will take care of problems.

EXAMPLE (this is the command I use to load Chromium 30):

```
/home/vindsl/.chrome-linux/chrome --disable-setuid-sandbox **[COLOR="#FF0000"]--user-data-dir=/home/vindsl/.config/chromium-canary[/COLOR]** --flag-switches-begin --flag-switches-end
```

---

### Post by 3dmatrix on 2013-07-12
> **VinDSL said:**
> ```
chrome://version/
```
...should show your profile path.  ;)

It shows the Profile Path	 as  /home/username/.config/chromium/Default
but as i mentioned in my first post i already delete the .config/chromium folder so where is it again getting the data from ?

---

### Post by vasa1 on 2013-07-12
> **3dmatrix said:**
> I am facing a strange problem since some days.
**On one of the partitions with Ubuntu 13.04** (with all updates done),...
.
As far as I can tell, you've done everything that *should* solve the problem. Since the problem *hasn't* been solved, I'm wondering about what you mean by the quoted part.

---

### Post by 3dmatrix on 2013-07-12
There are two partitions on my HDD, one with Ubuntu 12.04 and the other with 13.04. The one with 13.04 is facing this prob.
There must be some place where chromium saves data and is still not been deleted. And when it is reinstalled it is fetched back again.

---

### Post by vasa1 on 2013-07-13
What do you see at the top of the settings page? As far as I know, if you've deleted .config/chromium and still have a problem, there really isn't anything else to do if you are not synced in (as per the settings page). 

As a last resort, have you tried **first** deleting everything "from the beginning of time" in the screen that you see when you press ctrl+shift+delete  together (or Menu, Tools, Clear Browsing Data) and **then** exiting Chromium and **then** deleting .config/chromium-browser or .config/chromium?

---

### Post by 3dmatrix on 2013-07-14
I uninstall chromium (purge), delete .config and .cache files, empty the trash. Restart the comp and then reinstall chromium.
Still after reinstall the problem remains.

---

### Post by VinDSL on 2013-07-14
Hrm...

How does hosts file look?  Maybe a Facebook redirect snuck in there.

Here's mine...

```
vindsl@Zuul:~$ gksudo gedit /etc/hosts

```

```
127.0.0.1	localhost
127.0.1.1	Zuul
# The following lines are desirable for IPv6 capable hosts
# ::1     ip6-localhost ip6-loopback
# fe00::0 ip6-localnet
# ff00::0 ip6-mcastprefix
# ff02::1 ip6-allnodes
# ff02::2 ip6-allrouters
```

You said other browsers work okay, but... who knows?!?!?

---

### Post by farrinux on 2013-07-14
```
dpkg -L <packagename>
```

Should list the places where the files are at.

---

### Post by 3dmatrix on 2013-07-14
> **VinDSL said:**
> Hrm...

How does hosts file look?  Maybe a Facebook redirect snuck in there.

Here's mine...

```
vindsl@Zuul:~$ gksudo gedit /etc/hosts

```

```
127.0.0.1	localhost
127.0.1.1	Zuul
# The following lines are desirable for IPv6 capable hosts
# ::1     ip6-localhost ip6-loopback
# fe00::0 ip6-localnet
# ff00::0 ip6-mcastprefix
# ff02::1 ip6-allnodes
# ff02::2 ip6-allrouters
```

You said other browsers work okay, but... who knows?!?!?


127.0.0.1	localhost
127.0.1.1	usrname

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters


I am having no problem with Opera in accesing FB.
.

---

### Post by 3dmatrix on 2013-07-14
> **farrinux said:**
> ```
dpkg -L <packagename>
```

Should list the places where the files are at.

I will try that and get back !

---

