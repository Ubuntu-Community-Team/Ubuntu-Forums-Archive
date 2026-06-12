---
title: "Get firefox to update to 3.0"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by dgbearcat on 2008-06-27
I've actually been using Ubuntu for a while, but I can't seem to get this to work. I've got firefox 3.0 beta 5, but I'm reasonably sure that it shouldn't be a beta anymore. I've run updates and tried it through synaptec which seems to tell me that maybe I really am on the latest version. 

apt-get install firefox doesn't do anything but tell me I'm on the latest version, so perhaps I am just assuming that it shouldn't be a beta, but who knows.

---

### Post by bumanie on 2008-06-27
You must be using hardy to have FF3 beta5. Either > sudo apt-get update or System --> Administration --> Update manager and click on check. You are correct, FF3 final release came out about a week ago. There have been a number of other updates as well over the week.

---

### Post by Malta paul on 2008-06-27
To check your version of Firefox, Run Firefox go to help and click 'About Mozilla Firefox' :)

---

### Post by Aztek Blood on 2008-06-27
This happened to me also. Don't know if it is for the same reason.

I fixed it by going to System>Administration>Software Sources. In the "Download from:" option, select Server for United States or Main Server. Close and let it Reload the repository.

I used to select a server that was close. However, I think the server I selected wasn't updated. Selecting Server for United States fixed it for me. Hope it helps.

---

