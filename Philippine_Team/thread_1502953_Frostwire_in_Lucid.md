---
title: "Frostwire in Lucid"
date: 2010-06-06
forum: Philippine Team
---

### Post by justoxdizaola on 2010-06-06
ngkakaroon po ako ng problema sa "unsatisfiable dependencies" sa frostwire. kea po d q mainstall. pahelp nmn po tnx...

---

### Post by Script Warlock on 2010-06-06
baka di nyo pa nainstall ang java.

---

### Post by jepong on 2010-06-06
> **justoxdizaola said:**
> ngkakaroon po ako ng problema sa "unsatisfiable dependencies" sa frostwire. kea po d q mainstall. pahelp nmn po tnx...

try to install with the internet connected... automatic naman ddownload yan.

---

### Post by jaceleon on 2010-06-07
Meron nga konting problema regarding sa open source version ng java. why dont you download the sun-java6-jre and sun-java6-bin on the debian website then install the deb packages. Of course, remove the current java installed. Then fix the installation by doing this on terminal:

sudo apt-get install -f

kung tama ako (pakicorrect na lang kung mali), e iiinstall ng command na yan yung other dependencies ng java na yan. Once done, then install the .deb of frostwire and sasabihin niyan na dependencies satisfied.

By default, the Ubuntu Software Center always installs the open source (dummy) of Java. Yun yung problem.

Hope you do it well...

---

