---
title: "How to stop, blacklist a web site from intruding ?"
date: 2021-02-09
forum: New to Ubuntu
---

### Post by Innernet on 2021-02-09
Hello, good day !
Is there a way to forbid a website from ever intrude my system ?  It shows up sometimes when visiting a newspaper site, undesirable contents, probably part of the site peddling/mining/cookies/tracking/whatever.

---

### Post by CelticWarrior on 2021-02-09
Are you saying that a different website opens? Could be a "legitimate" popup of the website you're visiting but also malware.
Or it's adds served by the website you're visiting? That's normal and quite prevalent. Most or all can be avoided using certain extensions like Adblock.

---

### Post by #&amp;thj^% on 2021-02-09
I Block a Website Access on Linux Using the "/etc/hosts File"

The “/etc/hosts” file is a simple text file used by all operating systems to map hostnames to IP addresses.
For example, to block some of “facebook.com” and “twitter.com”, it is sufficient to add the following lines to your host file.
```

# vi /etc/hosts

0.0.0.0 www.facebook.com
0.0.0.0 www.twitter.com
0.0.0.0 twitter.com
```

Most of us can already use the 127.0.0.1, loopback address. It is used to establish an IP connection with the local computer.

When you block them, it is good to restart network service and flush the DNS cache on Linux.

Method-2: How to Block a Website Access on Linux Using iptables

Iptables is used to set up, maintain, and inspect the tables of IPv4 packet filter rules in the Linux kernel.

Use the following commands to block “facebook.com” using iptables on Linux.
```

# iptables -A OUTPUT -p tcp -d www.facebook.com --dport 443 -j DROP
# service iptables save
# service iptables restart
# iptables -L
```

Use the following commands to block “twitter.com” using iptables on Linux.
```

# iptables -A OUTPUT -p tcp -d www.twitter.com --dport 443 -j DROP
# iptables -A OUTPUT -p tcp -d twitter.com --dport 443 -j DROP
# service iptables save
# service iptables restart
# iptables -L
```

Method-3: How to Block Website Access on Linux Using Chomper

Chomper is a Python command-line that allows user to create a list of webistes to be blocklisted or whitelisted for specified periods of time.

This tool is especially developed to improve the user productivity on working hours by saving them from Internet distractions.

This allows you to block particular URLs as well.
Method-4: How to Block Website Access on Linux Using CTparental

CTparental is a parental control tool used to control how others can use a Linux computer.

You can easily manage this using a web interface ([https://admin.ct.local](https://admin.ct.local)).

---

### Post by Innernet on 2021-02-09
Celtic Warrior : It shows at the bottom left of screen when visiting certain legitimate sites; nothing obscure, obscene nor dirty :  Handshaking with such and such... and slowing everything.  Other times had a yellow banner at top showing "A web site is preventing from downloading... Do you want to stop it ?"...   I would prefer the option "Do you want to destroy it ?" :roll:  _And how to find which is the identity of the site undisclosed-by-the-browser_ for that yellow banner ?

Thank you 1fallen !
Will digest your suggestions slowly to implement properly. Am not very skilled, but your guidance seems good for beginners.

---

### Post by SeijiSensei on 2021-02-09
If you're using Firefox, I recommend both the [Ghostery]("https://addons.mozilla.org/en-US/firefox/addon/ghostery/") and [uBlock Origin]("https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/") add-ins.

---

### Post by crip720 on 2021-02-09
Does sound like an ad site that certain sites use.  I use UBlock and every so often when trying to go to a site, will get a blank page for I what I think is ad site(different name from original site).  If main site is important for you to see, might have to put up with it, or see if you can get information from another nicer site.

---

### Post by #&amp;thj^% on 2021-02-10
Finding URL's for pop-up, pop-over, pop-under's can be a bit of a trick. 

SeijiSensei's suggestion is a good one for that kind of pop-up crap we find on our favorite sites.
I tend to be a bit more investigative, I want to know more of these types of redirects.
_I have to be very careful on how much info I can provide to you here._
My sore spot comes from sites that think I need to view Videos while I'm visting their page then I'll look at the elements the site renders.
Example:
```
</script><!-- End Custom Dimension dataLayer --><script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "WebPage",
  "@id": "https://smallbusiness.chron.com/out-popups-coming-computer-70027.html",
  "url": "https://smallbusiness.chron.com/out-popups-coming-computer-70027.html",
  "name":"How to Find Out Where Pop-Ups Are Coming From on a Computer",
  "breadcrumb":{
    "@type":"BreadcrumbList",
    "itemListElement":[
      {
        "@type": "ListItem",
        "position": 3,
        "item": {
          "@type": "Website",
          "@id": "https://smallbusiness.chron.com/computers/",
          "url": "https://smallbusiness.chron.com/computers/",
          "name": "Computers"
```
Find the offending URL and block it.
So I think the best option is the Ad and Popup blockers that has been already suggested. 
Pop-up Tips

Modern Web developers have the ability to display windows that look like pop-ups but are nothing more than regular HTML elements called divs. If you visit a site that displays image thumbnails, a larger version of the image may appear in a box that resembles a pop-up. The box may even have a border around it that seems to cast a shadow on the Web page below. Because these types of pop-ups are not browser windows or malware, they cannot harm your computer. They will disappear when you leave the Web page that made them appear.

---

### Post by Innernet on 2021-02-10
Thank you gentlemen.
SeijiSensei :  I avoid using Firefox as I perceive it as a tunnel to convey the slowing/halting intruders.  Opera seems smoother.
Like 6 years ago I installed an adblocker which was left out in an upgrade and made no difference without it, so have not used it again lately.

1fallen : Will see if I can follow your instructions on some clear mind moment.

---

