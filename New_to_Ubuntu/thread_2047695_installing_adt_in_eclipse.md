---
title: "installing adt in eclipse"
date: 2012-08-25
forum: New to Ubuntu
---

### Post by iamrcube on 2012-08-25
I have been trying to install ADT Plugin for android in eclipse 4.2 using the help menu. But when i try to install it from [this link]("https://dl-ssl.google.com/android/eclipse/") it gives the following error message:

Cannot complete the install because one or more required items could not be found.
  Software being installed: Android Development Tools 20.0.3.v201208082019-427395 (com.android.ide.eclipse.adt.feature.group 20.0.3.v201208082019-427395)
  Missing requirement: Android Development Tools 20.0.3.v201208082019-427395 (com.android.ide.eclipse.adt.feature.group 20.0.3.v201208082019-427395) requires 'org.eclipse.wst.sse.core 0.0.0' but it could not be found

Can anyone please suggest a solution.

---

### Post by hooligan8 on 2012-09-25
for correctly configure your system to programming with android, you must indicate where is the new skd, for this use this command
to the home write in shell

sudo gedit .bashrc

add this line at end of file

#AndroidDev PATH 
PATH=$PATH:$HOME/android-sdk-linux_x86/tools 
export PATH 

end execute 

source .bashrc

and now you can add the plugin to eclipse

---

