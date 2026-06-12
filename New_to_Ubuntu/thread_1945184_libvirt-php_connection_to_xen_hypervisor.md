---
title: "libvirt-php connection to xen hypervisor"
date: 2012-03-22
forum: New to Ubuntu
---

### Post by AleeRaza on 2012-03-22
Official Page: [http://libvirt.org/php/](http://libvirt.org/php/)
  From the above link, when I execute libvirt_version() to check  whether libvirt-php is working or not it gives me no warning or any  other error. Execute successfully and showing output as on the above  page:
    Libvirt-php Example:   [http://libvirt.org/php/examples.html](http://libvirt.org/php/examples.html)
  From the examples page, when I execute the Example "Get List of Domains"
  It gives me the following warnings in the output.
  Warning:  libvirt_connect() [function.libvirt-connect]: cannot recv  data: : Connection reset by peer in /opt/lampp/htdocs/xampp/hw.php on  line 2
  Warning:  libvirt_list_domains() expects parameter 1 to be resource, boolean given in /opt/lampp/htdocs/xampp/hw.php on line 3
  Warning:  libvirt_list_domains() [function.libvirt-list-domains]: Invalid arguments in /opt/lampp/htdocs/xampp/hw.php on line 3
    Why these warnings are raised. And why the above script not showing the list of all domains??:(

---

