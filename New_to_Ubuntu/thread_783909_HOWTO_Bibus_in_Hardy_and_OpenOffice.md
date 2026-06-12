---
title: "HOWTO: Bibus in Hardy and OpenOffice"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by shuttleworthwannabe on 2008-05-06
Hi there, I thought I would share my experince with the community of scientific writer.

Bibus information [here]("http://bibus-biblio.sourceforge.net/wiki/index.php/Bibus:Community_Portal") and [here]("http://bibus-biblio.sourceforge.net/wiki/index.php/Bibus_bibliographic_database"). Install as per [these]("http://bibus-biblio.sourceforge.net/wiki/index.php/Installation#Ubuntu") instructions.

1. Start Openoffice Writer
2. In Writer, go to tools>Options>OpenOffice>Security>Macro Security..> set it to "medium". [this is the critical step; without this, Bibus will not communicate with OOo Writer]
3. Start Bibus; set-up will ask you to "activate" the link between Bibus and OOo; a new ODF document will open and prompt you to accept macro's: "enable" it.
4. Accept the connection by clicking on the "accept..." button.
5. Proceed with the setup; choose SQLite database format [unless you chose the optional MYSQL]. give your database a name and save it in a conveneint location.
6. Close all instances of OOo, inclusing the quick launcher.
7. Restart OOo writer
8. Start Bibus; do a search. check if the references can be inserted in OOo.
9. Enjoy the fruits of the hard work...time to write that thesis now!
10. if you have proxy issues; see [this]("http://bibus-biblio.sourceforge.net/wiki/index.php/Pubmed_search"):
11. if you need proxy authentication use this format: export http_proxy="username: password @ [http://yourproxyserver](http://yourproxyserver) : port/"

All the best,
S

---

### Post by hyper_ch on 2008-05-06
if you format this a bit nicer then you could "report" it and ask to have it moved to the tutorials section :)

---

### Post by mj_ja55 on 2008-05-21
When I try to install Bibus, I get:
> The following packages have unmet dependencies:
  bibus: Depends: python-central (>= 0.6.6) but 0.6.5ubuntu1 is to be installed
E: Broken packages


I can't find a way to install python-central 0.6.6.  What am I missing here?

---

### Post by shuttleworthwannabe on 2008-05-22
How are u installing Bibus? the best way I found is to add bibus repo's to the sources list; then 
sudo aptitude update and sudo aptitude install bibus; all dependencies should be taken care off.

---

### Post by mj_ja55 on 2008-05-22
I am trying to install bibus from the repository.   Here is the full output of my command line:

> mj@mjubuntu:~$ sudo apt-get install bibus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  bibus: Depends: python-central (>= 0.6.6) but 0.6.5ubuntu1 is to be installed
E: Broken packages


---

### Post by legatek on 2008-05-22
I also get this error in Gutsy.

---

### Post by Berneri on 2008-05-23
Hi guys,
the developper of bibus made it compatible with python-central version 0.6.5. It should work now.
If it still doesn't work, you may want to compile bibus from the sources. Assuming you have the bibus repository and the deb-src line uncommented, simply type:
apt-get source --compile bibus.
Then, just install the created bibus packages with Gdebi, dpkg, synaptic.

---

