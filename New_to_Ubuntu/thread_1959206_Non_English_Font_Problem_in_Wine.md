---
title: "Non English Font Problem in Wine"
date: 2012-04-15
forum: New to Ubuntu
---

### Post by 3dmatrix on 2012-04-15
I am trying to use a windows application named PABLO in wine under Ubuntu.

This application has to deal with English and Non English characters (Chinese etc)
It also has a flash animation running under it where it displays how that character is written.

As you can see in the attached pic. In some places the Chinese characters are displayed but in other places they are displayed as rectangular boxes. (marked in blue)

The text where it should have displayed w&#466; dispalys only w (marked in red)

The flash animation is missing (marked in green)

This application works fine in windows, so what could be done about the font problem ?
Seems it is not able to read the system non-english font. In Ubuntu there is no font problem, the problem is only in applications running in wine under Ubuntu.

---

### Post by arroyocallejas on 2012-04-15
ALTERNATIVE SOLUTION:

Hi. You have probably to install the Windows versions under Wine. But in my experience, Wine is not really useful as the audio-video-etc quality changes drastically, something worrying especially if you're using an app regularly. Then, I highly recommend you to use Virtualbox and then install Windows inside Ubuntu. It works great and as long as you don't use both Linux apps and Windows apps at the same time, it may work as if you were in Windows.

You can install Virtualbox via Software Center and then install Windows from a CD or .iso

---

### Post by 3dmatrix on 2012-04-15
> **arroyocallejas said:**
> ALTERNATIVE SOLUTION:

Hi. You have probably to install the Windows versions under Wine. But in my experience, Wine is not really useful as the audio-video-etc quality changes drastically, something worrying especially if you're using an app regularly. Then, I highly recommend you to use Virtualbox and then install Windows inside Ubuntu. It works great and as long as you don't use both Linux apps and Windows apps at the same time, it may work as if you were in Windows.

You can install Virtualbox via Software Center and then install Windows from a CD or .iso

I am obviously using the windows version of that application under wine. I do not need Audio Video support for that application. IF that stroke order animation works in it, it would be nice but the main problem is the FONT problem. How can we solve that ?

---

### Post by kazztan0325 on 2012-04-16
> **3dmatrix said:**
>  ..., it would be nice but the main problem is the FONT problem. How can we solve that ?

Hi 3dmatrix,

Have you copied any Chinese font to **/home/*username*/.wine/drive_c/windows/Fonts** folder?

If you have already done it, I have no other ideas at present, sorry. (Dui bu qi!)

---

### Post by 3dmatrix on 2012-04-16
> **kazztan0325 said:**
> Hi 3dmatrix,

Have you copied any Chinese font to **/home/*username*/.wine/drive_c/windows/Fonts** folder?

If you have already done it, I have no other ideas at present, sorry. (Dui bu qi!)

&#27809;&#20851;&#31995; &#65306;&#65289;
I copied some fonts but it didnt work. Its not only Chinese characters but also pinyin with tone marks that is not being displayed. e.g. In w&#466; only w is being displayed.
&#35874;&#35874;&#12290;

---

### Post by kazztan0325 on 2012-04-17
What about trying "wine packages with CJK patches"?
However I'm not sure if those packages would be able to fix your problem...

**"wine-cn" team >> wine-cn**
[https://launchpad.net/~wine-cn/+archive/ppa]("https://launchpad.net/~wine-cn/+archive/ppa")

Hope this helps.

---

### Post by 3dmatrix on 2012-04-17
> **kazztan0325 said:**
> What about trying "wine packages with CJK patches"?
However I'm not sure if those packages would be able to fix your problem...

**"wine-cn" team >> wine-cn**
[https://launchpad.net/~wine-cn/+archive/ppa]("https://launchpad.net/~wine-cn/+archive/ppa")

Hope this helps.

Are these packages available in Ubuntu Repo ?

---

### Post by kazztan0325 on 2012-04-17
> **3dmatrix said:**
> Are these packages available in Ubuntu Repo ?

No, unfortunately these are not available in Ubuntu Repo.

You need to add PPA to your 'Software Sources'.
Please refer to the way on following web page.

**What are PPAs and how do I use them?**
[http://askubuntu.com/questions/4983/what-are-ppas-and-how-do-i-use-them]("http://askubuntu.com/questions/4983/what-are-ppas-and-how-do-i-use-them")

---

### Post by sportfreak2020 on 2012-04-23
how about japanese characters ?? i m using a windows trading program with japanese characters .. everything works flawlessly after installing the japanese related fonts, except for few very important menu items .. do you guys think i m missing some fonts over here !?

---

