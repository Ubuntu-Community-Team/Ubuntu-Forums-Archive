---
title: "Dedicated Web Server Help"
date: 2014-04-05
forum: New to Ubuntu
---

### Post by Bill_Croxson on 2014-04-05
Hi there. I'm looking for an in-depth guide on setting up my own dedicated web server using ubuntu server lts. I do not know the current version, as I have to check the ISO for the version. However, I have searched for tutorials, but to me they seem out of date, with the latest one i found from 2010. I am preferably going to be using LAMP and OpenSSH as a base, and any help will be greatly appreciated. Do not hold back on the lingo. I am very tech-literate. Cheers!! :p
NOTE: Very sorry if this is in the wrong thread... this is my first thread on the forums. I will also be posting the version of ubuntu server that i will be using at a later point in time.

---

### Post by mcduck on 2014-04-05
.Here's the official server guide for the latest LTS version (12.04): [https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/)

That should cover both installng and configuring the LAMP stack and ssh

---

### Post by SeijiSensei on 2014-04-05
Another document on LAMP installation for Ubuntu: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Lars Noodén on 2014-04-05
What will you use the server for?  Regular web pages?  A content management system (Joomla, Drupal, Lenya, OpenCMS, etc.) ?  A wiki?  That will determine what you need to install and what can be ignored.  It'll be fairly easy to set up, but the choices differ according to the task.

---

### Post by Bill_Croxson on 2014-04-05
> **mcduck said:**
> .Here's the official server guide for the latest LTS version (12.04): [https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/)

That should cover both installng and configuring the LAMP stack and ssh
Thanks for the guide mcduck. It helped out alot!!

> **SeijiSensei said:**
> Another document on LAMP installation for Ubuntu: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
More info on LAMP. Cheers SeijiSensi!

> **Lars Noodén said:**
> What will you use the server for?  Regular web pages?  A content management system (Joomla, Drupal, Lenya, OpenCMS, etc.) ?  A wiki?  That will determine what you need to install and what can be ignored.  It'll be fairly easy to set up, but the choices differ according to the task.
Lars Nooden, I'm looking to initially use the server just for a few webpages with a shopping cart to sell some items. In the future, I'm looking to extend the server to be used for ftp and email hosting, and several web hosts using virtualization.

---

### Post by Lars Noodén on 2014-04-06
If you're looking for a web shop, you'll have to do a bit of research to find the kit that suits your needs.  osCommerce is one place to start looking but there are several others.  I'd [skip FTP](https://www.google.com/search?q=stop+using+ftp) and stay with SFTP.  It is supported by the file managers and other utilities and is built in to openssh-server which you already have.  Mail is a lot of work to do correctly, I'd consider having that hosted somewhere.

---

### Post by Bill_Croxson on 2014-04-06
Well, I was just thinking about using a bit of PHP and use SQL to store and transfer the item data. I was looking at FTP as I would provide cloud space to people. Is there anything simpler in ubuntu to do that?

---

### Post by Lars Noodén on 2014-04-06
> **Bill_Croxson said:**
>  Is there anything simpler in ubuntu to do that?

SFTP is a lot simpler to set up than FTP, all you need on the server side is the package openssh-server which I read you have already.  If you want to chroot users to specific directories that is easy too.  You users will find it easy to connect:  Try it with Nautilus, or other file manager, and go to the location bar (ctrl-L if necessary) and enter sftp://*user*@*xx.yy.zz.aa*, where you've substituted in the relevant username and address.  Besides the file managers, FileZilla works with SFTP and for legacy systems there is also WinSCP.  Mac users have CyberDuck.  SFTP is about as simple as you can get, you already have it.

With the shopping carts, the choice is spend a lot of time making a new one or spend a lot of time learning an existing one.  The advantage of some of the existing ones is that they've been around long enough to have many bugs smoothed out.  The advantage of the former is that you get exactly what you need, but don't handle the payments yourself, that is too risky these days IMO.  Use one of the APIs for Google Wallet, Skrill, Paypal or other payment system.  I have no clue how to handle Bitcoin.

---

