---
title: "OpenOffice preffered"
date: 2012-06-27
forum: New to Ubuntu
---

### Post by czgirb on 2012-06-27
Today, I installed 12.04 and found I prefer **OpenOffice** to** LibreOffice**.
How can I **uninstalled Libre** and** installed OOo** (incld. **Base**)
Please guide me ....

---

### Post by KIAaze on 2012-06-27
This should do it:
```
sudo apt-get remove libreoffice*
sudo apt-get install openoffice.org

```

But you can have both installed and just change the default file associations:
Right-click a .ods/.odt/etc file -> Properties-> Open with -> Select openoffice -> set as default.

(For CLI and generic solutions, look up info on xdg-open, MIME types and gnome file associations (Gnome stores those things somewhere else. I had to look it up recently, but don't remember the files now. Will post as soon as I find it again.))

---

### Post by stlsaint on 2012-06-27
You mean something other than removing with Ubuntu Software Center?

---

### Post by czgirb on 2012-06-27
> **KIAaze said:**
> This should do it:
```
sudo apt-get remove libreoffice*
sudo apt-get install openoffice.org

```But you can have both installed and just change the default file associations:
Right-click a .ods/.odt/etc file -> Properties-> Open with -> Select openoffice -> set as default.

(For CLI and generic solutions, look up info on xdg-open, MIME types and gnome file associations (Gnome stores those things somewhere else. I had to look it up recently, but don't remember the files now. Will post as soon as I find it again.))

Is it will** install all openoffice (incld. openoffice base)**?
thank you.

---

### Post by vasa1 on 2012-06-27
I'm not sure the advice being offered here is correct. I would suggest that the OP be cautious.

Edit: you can see what will be installed by running a simulation first. You don't need sudo for this since nothing will actually be installed.

```
apt-get install -s openoffice.org
```
You'll get back LibreOffice.

---

### Post by vasa1 on 2012-06-27
I have **not done** what I'm suggesting below but I **think** it is correct.

**apt-get purge -s libreoffice*** will show you what all will be removed if you type the actual command which is
**sudo apt-get purge libreoffice***
Then, there's the matter of your profile which is in your home directory and is **not** removed by purge. That should be here:
[B]~/.config/libreoffice/
[/B]IMO, if you want a clean start, delete the folder and its subfolders.

Then, head off to [http://www.openoffice.org/download/index.html](http://www.openoffice.org/download/index.html) and get what you want.

I would be **extremely reluctant** to keep **both** LibO and OpenOffice on my computer since I have the impression there could be problems. I don't see the need for both. I don't see the need to fiddle with associations and mime-types.

Obviously, it's your decision :)

---

### Post by KIAaze on 2012-06-27
Oh, ok, I see the problem now: All the openoffice packages are just transitional dummy packages depending on the corresponding libreoffice packages, i.e. openoffice is not even in the repos anymore!

In that case, as vasa1 said, you will have to get it from the official website.

So remove all libreoffice/openoffice packages:
```
# simulate (good tip from vasa1)
apt-get remove -s openoffice.org-* libreoffice-*
# remove if you agree with what the simulation removes
sudo apt-get remove openoffice.org-* libreoffice-*

```
Note: You can use the official package manager (software centre) or synaptic for that (I prefer to use synaptic).
And then download and install openoffice from the official website.

> **vasa1 said:**
> 
I would be **extremely reluctant** to keep **both** LibO and OpenOffice on my computer since I have the impression there could be problems. I don't see the need for both. I don't see the need to fiddle with associations and mime-types.


I have an old Ubuntu 10.04 at work, which still uses openoffice, so I installed libreoffice manually there and have been using both side by side for months without any issues. My main issue was getting Ubuntu to use the custom libreoffice install as default office application, hence the mention of MIME types, etc.
I often imported MS documents in both to get the best result, but unfortunately I got the same problems in both most of the time. Installing official MS office viewers via wine worked better.

---

### Post by vasa1 on 2012-06-27
> **KIAaze said:**
> ...
I have an old Ubuntu 10.04 at work, which still uses openoffice, so I installed libreoffice manually there and have been using both side by side for months without any issues. My main issue was getting Ubuntu to use the custom libreoffice install as default office application, hence the mention of MIME types, etc ...
My reluctance to suggest keeping both is that one doesn't know the competence of the person receiving the suggestion and I felt that for the "average" user, one office suite should suffice. No doubt, people who know what they're doing may be able to juggle both.
And, in general, if one is determined to get rid of a software package, I understand that **purge** is more thorough than **remove**, removing config files as well. (The ones in the user's home aren't affected.)

---

### Post by SeijiSensei on 2012-06-27
I just did this yesterday by following [these instructions](http://www.upubuntu.com/2012/05/how-to-install-apache-openoffice-34-via.html).

First purge all of libreoffice and any components:

```
sudo apt-get purge libreoffice libreoffice-*
```

Next, install the upubuntu PPA and then openoffice like this:

```

sudo add-apt-repository ppa:upubuntu-com/office
sudo apt-get update
sudo apt-get install openoffice

```

Notice that the package is called simply "openoffice" and not "openoffice.org".

---

### Post by vasa1 on 2012-06-27
> **SeijiSensei said:**
> ...
First purge all of libreoffice and any components:
```
sudo apt-get purge libreoffice libreoffice-*
```
...
Could you please explain why 
```
sudo apt-get purge libreoffice*
```
won't suffice?

---

### Post by SeijiSensei on 2012-06-27
It might; did you try it?

---

### Post by vasa1 on 2012-06-27
> **SeijiSensei said:**
> It might; did you try it?In a way: see [http://ubuntuforums.org/showpost.php?p=12057221&postcount=6](http://ubuntuforums.org/showpost.php?p=12057221&postcount=6)

---

### Post by madjr on 2012-06-27
> **czgirb said:**
> Today, I installed 12.04 and found I prefer **OpenOffice** to** LibreOffice**.
How can I **uninstalled Libre** and** installed OOo** (incld. **Base**)
Please guide me ....

any hint on why you found you prefer it ?

---

### Post by KIAaze on 2012-06-27
> **vasa1 said:**
> Could you please explain why 
```
sudo apt-get purge libreoffice*
```
won't suffice?
I'm pretty sure it does.

Anyway, @czgirb:
-Use SeijiSensei's method if you want automatic updates and trust the [upubuntu PPA]("https://launchpad.net/~upubuntu-com").
-Install openoffice using [the official .deb packages]("http://www.openoffice.org/download/other.html") provided by openoffice.org otherwise.

[LIST]
[*]About purge vs remove:
"purge" removes system-wide configuration files, i.e. usually anything the package installs in /etc. So unless you edited some openoffice/libreoffice related files in /etc, there is no reason not to use "purge". Using "Remove" would leave such files.
User-specific configuration files are stored in "~/.config/libreoffice/" can only be removed manually as indicated by vasa1.
cf [man apt-get]("http://man.cx/apt-get") for extensive info.
[*]About PPAs: [https://help.ubuntu.com/community/PPA](https://help.ubuntu.com/community/PPA)
[*]Openoffice installation guide: [http://www.openoffice.org/download/common/instructions.html#linux-deb](http://www.openoffice.org/download/common/instructions.html#linux-deb)
But you probably just need to double-click the downloaded .deb and install it through the software centre.
[/LIST]

---

### Post by Hagar Delest on 2012-07-15
Have a look also here: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

When installed from their respective .deb packages, AOO and LibO can run in parallel without any problem. The profiles are completely different.

---

