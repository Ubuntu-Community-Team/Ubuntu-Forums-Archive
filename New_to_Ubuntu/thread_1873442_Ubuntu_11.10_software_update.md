---
title: "Ubuntu 11.10 software update?"
date: 2011-11-01
forum: New to Ubuntu
---

### Post by soylentcola on 2011-11-01
So I'm trying to update my software and continually seem to be running into this problem with it: I continually get a "Failed to download package files" error with the following details


Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/l/linux/linux-image-3.0.0-13-generic_3.0.0-13.21_amd64.deb](http://security.ubuntu.com/ubuntu/pool/universe/l/linux/linux-image-3.0.0-13-generic_3.0.0-13.21_amd64.deb) 404  Not Found [IP: 91.189.92.166 80]
Failed to fetch htp:/t/archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata-java_2011l-0ubuntu0.11.10_all.deb 404  Not Found [IP: 91.189.92.180 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2011l-0ubuntu0.11.10_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2011l-0ubuntu0.11.10_all.deb) 404  Not Found [IP: 91.189.92.180 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/u/unity/libunity-core-4.0-4_4.24.0-0ubuntu2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/u/unity/libunity-core-4.0-4_4.24.0-0ubuntu2_amd64.deb) 404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/u/unity/unity-services_4.24.0-0ubuntu2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/u/unity/unity-services_4.24.0-0ubuntu2_amd64.deb) 404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/u/unity/unity_4.24.0-0ubuntu2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/u/unity/unity_4.24.0-0ubuntu2_amd64.deb) 404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/u/unity/unity-common_4.24.0-0ubuntu2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/u/unity/unity-common_4.24.0-0ubuntu2_all.deb) 404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/empathy/nautilus-sendto-empathy_3.2.0.1-0ubuntu1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/e/empathy/nautilus-sendto-empathy_3.2.0.1-0ubuntu1_amd64.deb) 404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/empathy/empathy-common_3.2.0.1-0ubuntu1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/e/empathy/empathy-common_3.2.0.1-0ubuntu1_all.deb) 404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/l/linux/linux-headers-3.0.0-13_3.0.0-13.21_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/l/linux/linux-headers-3.0.0-13_3.0.0-13.21_all.deb) 404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/l/linux/linux-headers-3.0.0-13-generic_3.0.0-13.21_amd64.deb](http://security.ubuntu.com/ubuntu/pool/universe/l/linux/linux-headers-3.0.0-13-generic_3.0.0-13.21_amd64.deb) 404  Not Found [IP: 91.189.92.166 80]

Not entirely sure what the problem is here, but I can't update at all because of it.  Are my PPAs out of whack?

---

### Post by 2F4U on 2011-11-01
I just tried to open 

[http://security.ubuntu.com/ubuntu/pool/universe/l/linux]("http://security.ubuntu.com/ubuntu/pool/universe/l/linux/linux-image-3.0.0-13-generic_3.0.0-13.21_amd64.deb")

without problems. Maybe a temporary problem?

---

### Post by soylentcola on 2011-11-03
Still failing to open 1 day later. I can find the actual index (the root page) of the link but apparently the linux image I'm trying to find doesn't exist. hmm...

---

