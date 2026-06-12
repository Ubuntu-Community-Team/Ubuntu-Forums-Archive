---
title: "Updates don't stick"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by Palu on 2008-09-21
Ever since installing Ubuntu Hardy Heron I have been installing the updates regularly. Over time I wondered things like why Hal would be updated every single time. Eventually I noticed that Firefox 3.0 would be installed every time. The list of updates is now quite long and it takes a while. From what I can tell, _every_ update is installed every time. They don't "stick" between boots. :(

Ideas? Comments? Funny jokes?

---

### Post by oldos2er on 2008-09-21
Can you run this command in a terminal, and post the output here?

 sudo aptitude update && sudo aptitude upgrade

---

### Post by cariboo on 2008-09-21
You could check /var/cache/apt/archives to see if the files you are talking about are archived there, if they are they don't need to be downloaded again. 

Do you can any error messages when you do an update?

Jim

---

