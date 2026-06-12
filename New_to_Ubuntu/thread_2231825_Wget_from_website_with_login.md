---
title: "Wget from website with login?"
date: 2014-06-28
forum: New to Ubuntu
---

### Post by noahsdev on 2014-06-28
So there is this website that has about 10,000 documents that I need to download. They do not have a bulk download option so I would have to download them one by one. The files are at url's such as 'randomsite.com/files/220.docx', (the documents are simply labeled as numbers). If there was no login required I could run a for loop in a script and get them all. But, when I do this it tells me that I don't have permission (because I haven't logged in). How can I login and wget each file from the terminal?

---

### Post by coffeecat on 2014-06-28
What is the website? What are their terms of service? Bulk downloading of so many documents may not be permitted by their ToS.

---

### Post by SeijiSensei on 2014-06-28
You can use --user and --password to pass the authentication information to wget. I agree with coffeecat, though; you should probably contact the site's owner before trying to do this after reading its Terms of Service.

---

