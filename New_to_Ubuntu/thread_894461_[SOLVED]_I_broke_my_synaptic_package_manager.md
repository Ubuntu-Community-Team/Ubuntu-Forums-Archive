---
title: "[SOLVED] I broke my synaptic package manager"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by gettinoriginal on 2008-08-19
I think I did it while trying to install google earth in terminal, but now I cannot access synaptic at all, it gives me the following error.

E: Type '<html>' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I am currently running ubuntu with compiz, and don't know what the medibuntu.list is.

---

### Post by Sycron on 2008-08-19
type in a terminal
```
$ cat /etc/apt/sources.list.d/medibuntu.list
```
and post the output.

---

### Post by gettinoriginal on 2008-08-19
here is what I got as output:

<html>
<head>
<title>The WineHQ APT Repository</title>
</head>
<body>
<div align="center">
<h1>This is the WineHQ Apt repository</h1>

<p>For instructions on using the APT repository to keep updated with current Wine beta packages, <a href="http://winehq.org/site/download-deb">visit the WineHQ Ubuntu and Debian downloads page</a>.</p>

<h1>Direct links to the latest Wine Packages</h1>
<h3>Ubuntu Hardy (8.04): <a href="archive/ubuntu/hardy/wine_1.1.2~winehq0~ubuntu~8.04-2-0ubuntu1_i386.deb">1.1.2 i386</a> | <a href="archive/ubuntu/hardy/wine_1.1.2~winehq0~ubuntu~8.04-2-0ubuntu1_amd64.deb">1.1.2 amd64</a> | <a href="archive/ubuntu/hardy/wine_1.1.2~winehq0~ubuntu~8.04-2-0ubuntu1_lpia.deb">1.1.2 lpia</a></h3>
<h3>--<i>Ubuntu versions older than Hardy are no longer being updated</i>--</h3>
<h3>Ubuntu Gutsy (7.10): <a href="archive/ubuntu/gutsy/wine_1.0.0~winehq0~ubuntu~7.10-2_i386.deb">1.0.0 i386</a> | <a href="archive/ubuntu/gutsy/wine_1.0.0~winehq0~ubuntu~7.10-2_amd64.deb">1.0.0 amd64</a></h3>
<h3>Ubuntu Feisty (7.04): <a href="archive/ubuntu/feisty/wine_1.0.0~winehq0~ubuntu~7.04-2_i386.deb">1.0.0 i386</a> | <a href="archive/ubuntu/feisty/wine_1.0.0~winehq0~ubuntu~7.04-2_amd64.deb">1.0.0 amd64</a></h3>
<h3>Ubuntu Edgy (6.10): <a href="archive/ubuntu/edgy/wine_1.0.0~winehq0~ubuntu~6.10-1_i386.deb">1.0.0 i386</a></h3>
<h3>Ubuntu Dapper (6.06): <a href="archive/ubuntu/dapper/wine_1.0.0~winehq0~ubuntu~6.06-1_i386.deb">1.0.0 i386</a></h3>
<h3>--<i>Etch users will need to upgrade to testing to avoid missing some libraries</i>--</h3>
<h3>Debian Etch (4.0): <a href="archive/debian/etch/wine_1.1.1~winehq0~debian~4.0-1_i386.deb">1.1.1 i386</a> | <a href="archive/debian/etch/wine_1.1.1~winehq0~debian~4.0-1_amd64.deb">1.1.1 amd64</a></h3>

<p>For older packages, please visit <a href="archive/index.html">the package archive.</p>

<p><a href="http://www.winehq.org/">Click here to go back to WineHQ.org</a></p>

<p><i>Bandwidth and web hosting for this repository is graciously provided by <a href="http://www.budgetdedicated.com/">BudgetDedicated.com</a></i></p>

</div>

</body>
</html>

---

### Post by Elfy on 2008-08-19
The medibuntu list is 

> Medibuntu is a packaging project dedicated to distributing software that cannot be included in Ubuntu for various reasons, related to geographical variations in legislation regarding intellectual property, security and other issues: you must have installed it though :)

You don't actually need to post it as it is quite a standard error - open the file and delete the contents then save it.

```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```

When you have done that and closed the file, run these 2 from the terminal

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

If you don't run hardy , then replace the first line with a suitable one from here

[https://help.ubuntu.com/community/Medibuntu#Adding](https://help.ubuntu.com/community/Medibuntu#Adding) the Repositories

---

### Post by gettinoriginal on 2008-08-19
When I run the last command you gave me I get this at the end:

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

However, at least I have my synaptic package manager back, thank you.  But now when I do a search for medibuntu, there are still medibuntu libs in there, should there be ??

---

### Post by drs305 on 2008-08-19
> **gettinoriginal said:**
> When I run the last command you gave me I get this at the end:

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263


Try running this to add the proper key for wine:
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

---

