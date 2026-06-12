---
title: "problems with medibuntu"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by apotter303 on 2008-07-02
I was trying to install google earth and now can open the synaptic package manager. I get and error.

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '--23:42:53--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read.'

Is there a way to just remove all the files for medibuntu and start over, I keep trying to do that but it says I don't have the permissions.

Cheers

---

### Post by hyper_ch on 2008-07-02
just delete the medibuntu.list file.... that should do it

---

### Post by drs305 on 2008-07-02
The following is for hardy:
Do this to restore the medibuntu repository:
```
sudo mv /etc/apt/sources.list.d/medibuntu.list  /etc/apt/sources.list.d/medibuntu.list-bak
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

For other versions, visit the Medibuntu page:
[Repository Howto]("http://www.medibuntu.org/repository.php")

---

### Post by apotter303 on 2008-07-02
That worked. 

Thanks a lot

---

### Post by kansasnoob on 2008-07-02
> **drs305 said:**
> The following is for hardy:
Do this to restore the medibuntu repository:
```
sudo mv /etc/apt/sources.list.d/medibuntu.list  /etc/apt/sources.list.d/medibuntu.list-bak
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

For other versions, visit the Medibuntu page:
[Repository Howto]("http://www.medibuntu.org/repository.php")

Dang, you're good! Real good!!!!!!!!!!!!!!!

---

### Post by tonylinko on 2008-08-13
wow, that worked......thanks a lot :guitar::guitar:

---

