---
title: "The strange process [^$I$^]"
date: 2018-10-22
forum: New to Ubuntu
---

### Post by petrashenko on 2018-10-22
Hello.
I'm using Ubuntu 18.04 Desktop and Drupal 7 Web site on it. Recently I've encountered the strange activity among OS processes. Running the 'top' utility I can see a process named [^$I$^] eating 99% of the CPU. The screenshot is here: [IMG]https://photos.app.goo.gl/WyWUG9usPRzKon8f9[/IMG][IMG]https://photos.app.goo.gl/WyWUG9usPRzKon8f9[/IMG][https://photos.app.goo.gl/QDY8PCGNHKLRTksj7](https://photos.app.goo.gl/QDY8PCGNHKLRTksj7)

How to deal with it?

Thanks in advance.

Andrii.

---

### Post by dino99 on 2018-10-22
"www-data" refer to drupal

---

### Post by hackerb9 on 2018-10-22
I suspect that your site has been hijacked and is mining cryptocoins. It may also be serving up malware to visitors who view your site. I suggest you take it down immediately and run forensics. Do you have a strangely named program in your /tmp directory that is created whenever you run Apache? That's a common sign.

[Drupal-sites fall victim to cryptojacking campaigns/]("https://www.bleepingcomputer.com/news/security/drupal-sites-fall-victims-to-cryptojacking-campaigns/")

[Drupal PSA: Updating your site will not remove backdoors]("https://www.drupal.org/psa-2018-002")

[Drupalgeddon FAQ]("https://groups.drupal.org/security/faq-2018-002")

[Your drupal site got hacked, now what]("https://www.drupal.org/docs/develop/security/your-drupal-site-got-hacked-now-what")

After you've cleaned up and reinstalled from backup, make sure you have security updates automatically being installed. I do that on my Debian GNU/Linux server and it got the patch for this major exploit back in [February]("https://www.debian.org/security/2018/dsa-4123") and [March]("https://www.debian.org/security/2018/dsa-4156"), before it exploded into what people have been calling "Drupalgeddon". I couldn't find the record of when Ubuntu released a patch, but I presume it was also way before exploits were happening.

---

### Post by petrashenko on 2018-10-22
Thanks guys, I'll try to manage.

---

