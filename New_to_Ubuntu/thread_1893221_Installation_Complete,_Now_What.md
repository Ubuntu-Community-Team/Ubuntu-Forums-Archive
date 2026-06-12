---
title: "Installation Complete, Now What?"
date: 2011-12-09
forum: New to Ubuntu
---

### Post by joshswain123 on 2011-12-09
I successfully got Lubuntu 11.10 up and running!! :D Now what? Are there any specific packages I should install to make sure everything will work nicely, or should I just dive right in? lubuntu-restricted-extras was mentioned to me earlier, for Java and Flash compatability, but is there anything else I should get while I'm at it?

---

### Post by dFlyer on 2011-12-09
Look for Ubuntu restricted extras in the archives if your into music and dvd movies. You may also want to download w32codecs_20110131-0.1medibuntu3_i386.deb from the medibuntu web page. The rest is up to you and your interests.

---

### Post by bluexrider on 2011-12-09
> **joshswain123 said:**
> I successfully got Lubuntu 11.10 up and running!! :D Now what? Are there any specific packages I should install to make sure everything will work nicely, or should I just dive right in? lubuntu-restricted-extras was mentioned to me earlier, for Java and Flash compatability, but is there anything else I should get while I'm at it?

Dive right in, gee what else? Well 

Here: 

sudo apt-get update && sudo apt-get upgrade
sudo apt-get install ubuntu-restricted-extras[B]

Enable Full DVD Playback(Dual Layer DVD Support)[/B]

[LIST]
[*]Though installing the restricted extras  package will solve most of your problems, you may not be able to play  dual layer dvds yet in your Ubuntu.
[/LIST]
 
[LIST]
[*]For that, you need to install libdvdcss2 package from medibuntu repositories. Simply do the following in Terminal.
[/LIST]

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update 

sudo apt-get install libdvdcss2

---

### Post by MG&amp;TL on 2011-12-09
There's three choices for you to browse applications on Lubuntu, each with advantages and disadvantages.

1. Synaptic package manager. This can be highly technical, but it is pre-installed by default and very stable. You can browse applications by searching for them.

2. Ubuntu Software Centre. This is fine, user-friendly, and stable, but very heavy on resources. You can get it by opening a terminal (Accessories->Lxterminal) and typing:

```
sudo apt-get install software-center
```

3. Lubuntu Software Centre. This is user-friendly, and light on resources, but is quite experimental (I'm helping code for it now. :) ), and stuff will likely break on a regular basis. You can install it by following the instructions here:

[http://www.omgubuntu.co.uk/2011/09/lubuntu-software-center/]("http://www.omgubuntu.co.uk/2011/09/lubuntu-software-center/")

There is probably enough applications already to get you started, however.

---

### Post by wolfen69 on 2011-12-09
Something a lot of people may not know is that after enabling the medibuntu repos, you can do:
```
sudo apt-get install non-free-codecs
```
which gives you ubuntu restricted extras, plus even more stuff. It's the way to go if you're a multimedia junkie.

---

### Post by joshswain123 on 2011-12-09
@bluexrider

I received this error for all four codes you suggested:

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

--

> sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update 

And for this code, this error as well:

```
W: GPG error: http://packages.medibuntu.org oneiric InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

```

---

### Post by joshswain123 on 2011-12-09
@wolfen69

I got the same error again :/

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by MG&amp;TL on 2011-12-09
What else are you running?

The error's saying you can't have two things trying to use package managers at the same time.

---

### Post by joshswain123 on 2011-12-09
Well that makes more sense now I think, seeing as I had File Manager open to browse my filesystem. Could that have been the issue?

---

### Post by joshswain123 on 2011-12-09
Tried it without File Manager open, still gave the same message:

```
W: GPG error: http://packages.medibuntu.org oneiric InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by joshswain123 on 2011-12-09
I just realized that I still had Synaptic open...oops...

Tried it and that eliminated the package manager error, but this one still remains:

```
W: GPG error: http://packages.medibuntu.org oneiric InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

```

---

### Post by Rex Bouwense on 2011-12-09
You can get that message when you have two package managers open, i.e. Ubuntu Software Center and Synaptic Package manager or Lubuntu Software Center and trying to update from the terminal, etc.

My slow typing skills have enabled you to figure it out for yourself.

---

### Post by nothingspecial on 2011-12-09
Try this 

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
```

---

### Post by Rex Bouwense on 2011-12-09
By the way I was going to suggest something else.  You are not bound by the default install applications.  In other words, if you don't want Chromium and want Firefox instead.  Download and install Firefox and uninstall Chromium.  The same goes for email programs, burning programs, calender, etc.  The programs were chosen by someone.  Get what you want and uninstall the others.

---

### Post by joshswain123 on 2011-12-09
@nothingspecial

I'm not entirely sure what I just did...
Translate?

```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.CGGI8YEUky --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
gpg: requesting key 0C5A2783 from hkp server keyserver.ubuntu.com
gpg: key 0C5A2783: public key "Medibuntu Packaging Team <admin@lists.medibuntu.org>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1

```

--

@Rex

Well, I happen to LOVE Chromium :D Nice and streamlined, the way I like it. I did however download VLC, because I just find it to be amazing... 0:]

---

### Post by nothingspecial on 2011-12-09
> **joshswain123 said:**
> @nothingspecial

I'm not entirely sure what I just did...
Translate?



It imported the key you didn't have. Now do 

```
sudo apt-get update
```

Are there any errors ?

---

### Post by joshswain123 on 2011-12-09
As a side note:

Is there a way for Lubuntu to work with NetFlix, or am I out of luck for that? I'm not terribly concerned about it, it would just be convenient if it could work.

---

### Post by joshswain123 on 2011-12-09
No errors whatsoever! Thanks everyone :)

---

### Post by MG&amp;TL on 2011-12-10
> **joshswain123 said:**
> No errors whatsoever! Thanks everyone :)

Unfortunately, see here: [http://how-to.wikia.com/wiki/How_to_watch_Netflix_(Watch_Instantly)_in_Linux]("http://how-to.wikia.com/wiki/How_to_watch_Netflix_(Watch_Instantly)_in_Linux")

Sorry. :(

---

### Post by joshswain123 on 2011-12-10
Meh, it isn't a big deal :) Like I said, it's not terribly important, it would just be awesome if it worked :P

---

