---
title: "Determine source of installed package"
date: 2012-08-27
forum: Programming Talk
---

### Post by bcooperizcool on 2012-08-27
I'm not quite sure how to tell where a package was installed from in a debian based system.   

I know I can use 

```
apt-cache showpkg
```
To list it,  but it won't tell me if it was installed locally from a .deb or from online, as well as,  using this,  if you simply have the repository there,  it will show up as in there. So,  do any of you know how to tell the source it was installed from?  
Such as,  local,  or a specific repository? 

Sorry if this doesn't make much sense :/   say it's identifier if com.bcooperizcool.something, in one repo,  but it could be com.johnSmith.something in another repo.   I know I can  check if com.johnSmith.someting is installed, but I don't and won't always know what the "johnSmith "  is.    

Or, list all installed packages from a specific source, so I could see if it was installed from there.

---

### Post by Bachstelze on 2012-08-27
AFAIK Apt does not keep track of where a package was installed from. What exactly do you want to do?

---

### Post by bcooperizcool on 2012-08-27
I was hoping to use this as part of a very simple license program,  it would only run a needed part of the code if it was installed from a specific source. (the code to generate a license key,  but I don't need to get into that as it doesn't affect what this needs to do)

---

### Post by Bachstelze on 2012-08-27
You should rethink your design, then. Even if Apt did keep track of where a package was installed from, that data would be easy to fake.

---

### Post by bcooperizcool on 2012-08-27
Do you have any suggestions for things I could look into to make sure my package is actually installed right?   Like,  from my source?

Edit: I couldn't figure it out,  so I'm going with what he said.  I am looking into other ways.

---

