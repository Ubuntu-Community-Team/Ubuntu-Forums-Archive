---
title: "Eclipse plugin installation problem"
date: 2006-11-26
forum: Programming Talk
---

### Post by jrjazzman on 2006-11-26
Hi,

I'm running Eclipse 3.2.1.  My end goal is to get the WTP stuff installed.  My first task was installing the pre-reqs listed, which were EMF 2.2.1, GEF 3.2.1 and JEM 1.2.1.  I've installed these and they show up in the configuration.  I then installed WTP, however when I go to file > new project, Web stuff is not there.  Also, any attempt to use Eclipse's plugin update feature results in a long list of missing components (see bottom of post).  Oddly, I've installed these and they are listed in help > about > plug-ins.

This is my first attempt at doing anything other than basic java apps w/ eclipse.  Not sure why getting these plugins running is such a booger, but I'd appreciate any help.  Thanks.



Current configuration contains errors that are not corrected by the requested operation and more errors would be introduced. See details for more information.
  ----- Current configuration problems -----
    JST Server Core (1.5.2.v200610070620--2PD88P9LCN7787) requires feature "org.eclipse.emf (2.2.0)", or equivalent.
    WST XML Core (1.5.1.v200608082030--3YIAAYAjGLENFH) requires feature "org.eclipse.emf (2.2.0)", or equivalent.
    WST XML UI (1.5.2.v200610071830-zkiCc0C2eGeGexE) requires feature "org.eclipse.gef (3.2.0)", or equivalent.
    WST Common Core (1.5.2.v200610140800--AXrVWXbElCl05G) requires feature "org.eclipse.jem (1.2.0)", or equivalent.
    Visual Editor (1.2.0.v20060530_RC2-0-a2N7MMl7) requires feature "org.eclipse.emf (2.2.0)", or compatible.
    WST Web Core (1.5.2.v200610140800--4hNDDhEmKWFYQL) requires feature "org.eclipse.emf (2.2.0)", or equivalent.
    WST Web Services UI (1.5.2.v200610070620-hai7Do_y98HDOuI) requires feature "org.eclipse.gef (3.2.0)", or equivalent.
    WST Common UI (1.5.2.v200610140800-qKHiTHohjmcJ67O) requires feature "org.eclipse.gef (3.2.0)", or equivalent.
    JST Enterprise Core (1.5.2.v200610140800--2PD88PA8APDAGS) requires feature "org.eclipse.emf (2.2.0)", or equivalent.
    WST Relational Database Core (1.5.2.v200610171240--3YIAAYCNETEZLJ) requires feature "org.eclipse.emf (2.2.0)", or equivalent.
    JST Web Core (1.5.2.v200610070620--87cMN7RkU-WXcu) requires feature "org.eclipse.emf (2.2.0)", or equivalent.
    JST Enterprise UI (1.5.2.v200610070620-pEBq_k_B5F5vHf6) requires feature "org.eclipse.emf (2.2.0)", or equivalent.
    WST Web Services Core (1.5.2.v200610140800--4hNDDhEmGSKJHa) requires feature "org.eclipse.emf (2.2.0)", or equivalent.
    WST Relational Database Adapters (1.5.2.v200610171240--Cq0bcpjKsVtauY) requires feature "org.eclipse.emf (2.2.0)", or equivalent.
  ----- Configuration problems after the operation -----
    JST Server Core (1.5.2.v200610070620--2PD88P9LCN7787) requires feature "org.eclipse.emf (2.2.0)", or equivalent.
    WST XML Core (1.5.1.v200608082030--3YIAAYAjGLENFH) requires feature "org.eclipse.emf (2.2.0)", or equivalent.
    WST XML UI (1.5.2.v200610071830-zkiCc0C2eGeGexE) requires feature "org.eclipse.gef (3.2.0)", or equivalent.
    WST Common Core (1.5.2.v200610140800--AXrVWXbElCl05G) requires feature "org.eclipse.jem (1.2.0)", or equivalent.
    Visual Editor (1.2.0.v20060530_RC2-0-a2N7MMl7) requires feature "org.eclipse.emf (2.2.0)", or compatible.
    WST Web Core (1.5.2.v200610140800--4hNDDhEmKWFYQL) requires feature "org.eclipse.emf (2.2.0)", or equivalent.
    WST Web Services UI (1.5.2.v200610070620-hai7Do_y98HDOuI) requires feature "org.eclipse.gef (3.2.0)", or equivalent.
    WST Common UI (1.5.2.v200610140800-qKHiTHohjmcJ67O) requires feature "org.eclipse.gef (3.2.0)", or equivalent.
    JST Enterprise Core (1.5.2.v200610140800--2PD88PA8APDAGS) requires feature "org.eclipse.emf (2.2.0)", or equivalent.
    WST Relational Database Core (1.5.2.v200610171240--3YIAAYCNETEZLJ) requires feature "org.eclipse.emf (2.2.0)", or equivalent.
    JST Web Core (1.5.2.v200610070620--87cMN7RkU-WXcu) requires feature "org.eclipse.emf (2.2.0)", or equivalent.
    JST Enterprise UI (1.5.2.v200610070620-pEBq_k_B5F5vHf6) requires feature "org.eclipse.emf (2.2.0)", or equivalent.
    WST Web Services Core (1.5.2.v200610140800--4hNDDhEmGSKJHa) requires feature "org.eclipse.emf (2.2.0)", or equivalent.
    WST Relational Database Adapters (1.5.2.v200610171240--Cq0bcpjKsVtauY) requires feature "org.eclipse.emf (2.2.0)", or equivalent.
    Eclipse Modeling Framework (EMF) Examples (2.2.0.v200609210005) requires feature "org.eclipse.emf (2.2.0)", or compatible.

---

### Post by fede77 on 2007-05-17
I am having exactly the same issue: 
WST Common UI (1.5.4.v200704150119-qKHiYJJQ6hbGi-5) requires feature "org.eclipse.gef (3.2.0)", or equivalent.

---

### Post by fede77 on 2007-05-17
I removed it using Add-remove.
Then downloaded from [http://www.eclipse.org/downloads/](http://www.eclipse.org/downloads/) 
tar zxfv eclis....tar.gz 
./eclipse 

Works just fine now.

---

### Post by gos1 on 2008-03-10
no need to do that . Just take a look at the requirements before installing the packages .For example in this line 
 
 JST Enterprise Core (1.5.2.v200610140800--2PD88PA8APDAGS) requires feature "org.eclipse.emf (2.2.0)", or equivalent.

it tries to tell you to select the emf package first to install the web tools package

---

### Post by RayDeCampo on 2008-08-29
Sorry for resurrecting an old thread, but I thought other would benefit from knowing which modules are the required dependencies:

Eclipse Modeling Framework
EMF Service Data Objects (SDO)
Java EMF Model
Graphical Editing Framework
XML Schema Infoset Model

It would be nice if the Eclipse installer had an option to automatically install dependencies.

---

### Post by dkaplowitz on 2008-11-09
And just to tack on to the post above mine, I just selected the package I wanted to install, then when I got that warning I chose "select required" and it automagically selected all the dependencies I needed. So it looks like the auto-dependency thing is a single click now.

Best,

Dave

---

### Post by teramind on 2009-10-01
If I klick on that button nothing happens...

---

