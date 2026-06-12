---
title: "Does Ubuntu ISO contain already all security updates?"
date: 2022-12-29
forum: New to Ubuntu
---

### Post by empleat on 2022-12-29
Hello,

I wonder when I download Ubuntu ISO, does it already contain all security, or even all updates (up to date)? Or do you have to update rest of small updates with the Update program? After you install OS??? If that is not the case, is there some other distro which updates ISO download with all up to date updates?

Thanks!

---

### Post by ian-weisser on 2022-12-29
See for yourself: The creation date of each image is at [http://cdimage.ubuntu.com/ubuntu/releases/](http://cdimage.ubuntu.com/ubuntu/releases/)

---

### Post by empleat on 2022-12-29
What when I clicked on 22.10/releases - there are only serve install ISOs: [http://cdimage.ubuntu.com/ubuntu/releases/22.10/release/ ]("http://cdimage.ubuntu.com/ubuntu/releases/22.10/release/")

Also even if there were today dates, does it mean it has security updates, or all updates? I can't really know that from looking at date.

---

### Post by QIII on 2022-12-29
Look [here]("https://releases.ubuntu.com/kinetic/") for the other downloads.

If you are fairly new to Ubuntu, I would recommend that you install a Long Term Support (LTS) release. The most recent is 22.04, Jammy Jellyfish, which you can find [here]("https://releases.ubuntu.com/22.04/").  Non-LTS releases of vanilla Ubuntu are only supported for 9 months.  LTS releases of Ubuntu are supported for 5 years.

In either case, the installation images are frozen as of the date of the release.  You must update them after they have been installed to get all the security and/or software updates.

---

### Post by guiverc on 2022-12-29
Daily images are available (*with all updates included up to the time of the start of the ISO build*), however those *dailies* are intended for QA (*Quality Assurance*) testing and come with no guarantees.  They are created for *unreleased* products, thus may contain problems (*the purpose of the QA performed on them*).

Multiple *daily* ISOs exist, eg. the major focus may appear to be on *lunar* or what will be released as Ubuntu 23.04 in 2023-April, but there is also the *jammy* ISO which will be 22.04.2 on release.

If other *distributions* have fully-updated ISOs like this, they'll likely also be intended for QA & thus may contain *undiscovered *bugs just like the Ubuntu ones do. Creating *daily* images costs resources to create them, thus there is almost always a reason (ie. QA).  If you prize *stability* and *security*, daily ISOs are generally not the answer.

FYI:   the term *daily* may mean once per day, but it's more a term representing *interval*, as you can have more than 1 *daily* built on a day (ie. if problems are found, it's late in the cycle & a fix needs to be quickly tested).

If helpful - I'll provide the ISO QA tracker - [http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)  but ISOs are found where expected; ie. cdimage.ubuntu.com of course.

---

### Post by empleat on 2022-12-29
OK so 10/20 that's pretty old, I read Ubuntu gets updates like every week!

Yeah that's what I was afraid of, I need actual system!

Since you can't update live USB this is a problem. But that's all I wanted to ask anyways!

Thanks this answers my question!

Also to guiverc, yeah i priritize security, i will try another thing. Thanks!

---

### Post by guiverc on 2022-12-29
You know you can have a *live* system with persistence... ie. write the *ISO* to media and use it as if it's an installed system, allowing you to apply upgrades etc.

 Whilst it's not identical to an installed system (ie. it's still run as *live* but with the changes made COW (*copy on write*) as per a normal *live* run, but those changes saved in the *persistence* area of the media and not only RAM (ie. the original media isn't altered if new packages exist, the newer copies being saved in persistence area & used instead), thus those updates will be found & used on next boot (*unlike a normal live system*).

I've used a *live* system on thumb-drive for >18 months, mostly as a carry-around system which I'd use on *borrowed* systems when away from office/home.  I no longer use *persistence *regularly (*except for some rare QA*) as I nearly always have *dailies* available & use them instead as it allows me to do the QA at the same time as I do my work (*when away from office/home*)

---

### Post by Topsiho on 2023-01-09
The iso's are only updated up to the time that they are released. 
This applies also to the daily builds of an ubuntu version that is under construction.
So after installation first thing to do is updating the install.
To prevent massive updates once in a while a point release is available: an iso updated to a date some months later.
As an example, the latest point release for ubuntu 22.04 is 22.04.1 that was released a few months (August?) after the first release in April.

That's all ...

Topsiho

---

