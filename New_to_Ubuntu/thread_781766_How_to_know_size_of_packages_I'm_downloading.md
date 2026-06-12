---
title: "How to know size of packages I'm downloading?"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by manojks on 2008-05-04
Guys, I'm just 3 days into Ubuntu. This is the first non-Windows OS I'm using. Now I'm just playing around with it, trying out new things and installing new softwares through **Add/Remove Applications**.

But I've got one problem. I have a connection with a **Download Limit** of 1.2 GB. So I need to know the size of softwares I'm installing. Is there some way to do that?

---

### Post by Monicker on 2008-05-04
I don't think you can see that informatoin using Add/Remove Application, as the interface was designed to be very simplistic.   You can see the package size if you use Synaptic; right click the package and select Properties and at the bottom it will show you the download size.

---

### Post by mikewhatever on 2008-05-04
I doubt Add/Remove has that feature, but Synaptic does. It's a column you have to enable under Settings->Preferences->Columns and Fonts, look for Download size. Add/Remove is a nice program to search for something in the repositories, read descriptions, etc, but to get more info on the size of packages and dependencies, it's better to use Synaptic.

---

### Post by manojks on 2008-05-04
Thanks. I think I got my answer.

---

### Post by szymon_g on 2008-05-04
type:

sudo aptitude upgrade 

or

sudo aptitude install name_of_package_you_wanna_to_install

and you will get something like that:

Do pobrania 208MB archiwów. Zaj&#281;te po rozpakowaniu: 962MB.

(of course, you will get answer in english /or in your locale langueage, if its not english)

it means:

to download : 208MB . After installation 962MB will be occupied.

---

### Post by manojks on 2008-05-05
> **szymon_g said:**
> type:

sudo aptitude upgrade 

or

sudo aptitude install name_of_package_you_wanna_to_install

and you will get something like that:

Do pobrania 208MB archiwów. Zaj&#281;te po rozpakowaniu: 962MB.

(of course, you will get answer in english /or in your locale langueage, if its not english)

it means:

to download : 208MB . After installation 962MB will be occupied.

It will install the package or what? I typed opera as the package's name. Nothing like that showed up.

---

### Post by mikewhatever on 2008-05-05
Opera is not in the repositories enabled by default. It's in one of the third party ones, partner or something, I am not sure. Here's a good help page for installing opera -> [https://help.ubuntu.com/community/OperaBrowser?highlight=%28opera%29](https://help.ubuntu.com/community/OperaBrowser?highlight=%28opera%29).

---

