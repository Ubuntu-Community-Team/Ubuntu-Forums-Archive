---
title: "Weblogic 8.1 EJB Deployment"
date: 2009-11-23
forum: Programming Talk
---

### Post by andrew222 on 2009-11-23
Somehow in Weblogic 8.1, when I click on "EJB Modules" I see no EJB's deployed (I have undeployed it).

However, when I try to deploy the stateless session bean, I get a message saying:

"The name you have specified is in use. Please enter a unique name." 

If I click on the link "Deployments", I see the the name of the EJB listed along with a couple of .war files I've deployed.  The deployment type listed for the EJB is shown as "UNKNOWN" but for the .war files they are being listed as what they are supposed to be listed as -- "Web Application".

I can not find a way to remove/undeploy the listing having the name of my EJB with "UNKNOWN" as the deployment type.

I need to solve this problem so I can get the EJB deployed.  Please let me know if you know the solution to this.

---

### Post by slavik on 2009-11-24
ooh not fun. why are you still on 8.1?

what you can do is, undeploy it, shut down the admin server, then remove any files it might have staged, start the admin server up.

if all else fails, you will need to remove the built in ldap (the data dir) and have weblogic rebuild it from config files.

Also, try using update ...

---

### Post by andrew222 on 2009-11-24
Thank you for the reply.  Please may I know how I can locate the data dir/ldap?

---

### Post by andrew222 on 2009-11-24
I went into config.xml and msi-config.xml and deleted the appropriate <Application> element and now all is well.

---

### Post by slavik on 2009-11-24
looks like weblogic didn't update the config.xml when you undeployed it. (9.2+ have a button that activate all changes).

the dir should be $DOMAIN_ROOT/$SERVER_NAME/data

---

