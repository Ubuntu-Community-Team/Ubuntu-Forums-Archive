---
title: "[SOLVED] php, apache, mysql configuring help plz"
date: 2007-11-27
forum: Philippine Team
---

### Post by Pedro0727 on 2007-11-27
i've done installing php, apache, mysql... but  hnd ko maconfig bcoz hnd 
ko alam kung saan or what command to use..
help plz.. i try to run the "mydms" error ang nakuhako..:confused:

---

### Post by mitchi on 2007-11-27
kung mula sa synaptic mo download, auto-configure na yan. Ready to use na yan agad. Kung manual downlad per package, just refer to the instructions per Linux distro sa main site nila.

Pinaka-convinient pa rin kung mula sa synaptic. It works for me, and my colleagues.

---

### Post by pinoyskull on 2007-11-27
> **Pedro0727 said:**
> i've done installing php, apache, mysql... but  hnd ko maconfig bcoz hnd 
ko alam kung saan or what command to use..
help plz.. i try to run the "mydms" error ang nakuhako..:confused:
meron ka bang guide na sinusundan?

---

### Post by Pedro0727 on 2007-11-27
> **pinoyskull said:**
> meron ka bang guide na sinusundan?

Wala po sir..
ok n po tnx po ng marami sainyo. May nakaligtaan lng ako n e install ung phpmyadmin :) working n lahat php, mysql and  apache.
IT WORKS!!!! hehehe

---

### Post by Pedro0727 on 2007-11-27
Ooops problem again! mga sir pano mag save dun s folder n www restricted kc..:confused:
location nya."usr/share/mydms/www"

---

### Post by outkast08 on 2007-11-27
Let me see baka tama ako, sa tingin ko root ang me ari nung folder na yun at wala write access yung user na gamit mo... :rolleyes: hmmm.... kung simple copy ng file from my Home folder.... example me file ako na foo sa home folder ko tapos Home Directory ko ang current na Directory sa Console ilipat ko siya sa usr/share/mydms/www.
 **sudo cp foo usr/share/mydms/www/foo**
Para mas graphical try mo **sudo nautilus**
Kung gagawa ka ng file gamit ang isang editor halimbawa Gedit. **sudo Gedit**

---

### Post by Pedro0727 on 2007-11-28
Maraming salamat po sir Outkast. ok n po, i can edit a file and save it der..
:)

---

### Post by Samhain13 on 2007-11-29
Uy, madagdagan ko lang. Kung magbubukas ng isang application na may graphical interface as root/super user, mas mabuting gamitin daw ang **gksudo**.

Mga halimbawa:
```

gksudo nautilus
gksudo gedit

```

Heto ang isa sa mga references kung bakit: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo).

---

### Post by outkast08 on 2007-11-29
> **Samhain13 said:**
> Uy, madagdagan ko lang. Kung magbubukas ng isang application na may graphical interface as root/super user, mas mabuting gamitin daw ang **gksudo**.

Mga halimbawa:
```

gksudo nautilus
gksudo gedit

```

Heto ang isa sa mga references kung bakit: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo).

tnx Samhain13 for the new input... :-D

---

### Post by Samhain13 on 2007-11-29
Walang anuman.

Pero matanong ko lang, ano yung /usr/share/mydms/www? wala yata ako nung directory na yun. Ang default directory ng web server ko ay /var/www.

Na-curious lang po. :)

---

