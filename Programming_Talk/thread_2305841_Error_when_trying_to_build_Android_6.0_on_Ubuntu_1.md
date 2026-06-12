---
title: "Error when trying to build Android 6.0 on Ubuntu 14.04 VM"
date: 2015-12-09
forum: Programming Talk
---

### Post by Wickie_Lee on 2015-12-09
I am not sure if this is the correct forum to post this question in. Anyway, I recently made an Ubuntu 14.04 LTS VM for building Android. However when trying to compile I am getting the following errors. I have tried looking around on the internet to see if I could find a solution, but could not find anything, Any help would be greatly appreciated.

```
Starting build with ninja
ninja: Entering directory `.'
[  0% 1/30186] target Java: framework ...ARIES/framework_intermediates/classes)
FAILED: /bin/bash out/target/common/obj/JAVA_LIBRARIES/framework_intermediates/classes-full-debug.jar.rsp
frameworks/base/core/java/android/security/FrameworkNetworkSecurityPolicy.java:32: error: isCleartextTrafficPermitted() in FrameworkNetworkSecurityPolicy cannot override isCleartextTrafficPermitted() in NetworkSecurityPolicy
    public boolean isCleartextTrafficPermitted() {
                   ^
  overridden method is static
frameworks/base/core/java/android/security/FrameworkNetworkSecurityPolicy.java:31: error: method does not override or implement a method from a supertype
    @Override
    ^
frameworks/base/core/java/android/security/NetworkSecurityPolicy.java:63: error: cannot find symbol
        return libcore.net.NetworkSecurityPolicy.getInstance().isCleartextTrafficPermitted();
                                                ^
  symbol:   method getInstance()
  location: class NetworkSecurityPolicy
frameworks/base/core/java/android/security/NetworkSecurityPolicy.java:76: error: cannot find symbol
        libcore.net.NetworkSecurityPolicy.setInstance(policy);
                                         ^
  symbol:   method setInstance(FrameworkNetworkSecurityPolicy)
  location: class NetworkSecurityPolicy
Note: Some input files use or override a deprecated API.
Note: Recompile with -Xlint:deprecation for details.
Note: Some input files use unchecked or unsafe operations.
Note: Recompile with -Xlint:unchecked for details.
4 errors
ninja: build stopped: subcommand failed.
make: *** [ninja_wrapper] Error 1

#### make failed to build some targets (02:10 (mm:ss)) ####


```

---

### Post by Miroslaw_Radziszew on 2015-12-30
Hi,
  I did not know about ninja build system. I suggest to read note carefully. It suggest to compile source files with options 
-Xlint:deprecation and -Xlint:unchecked 
for details. Try to add this flags to your compiler command. You must be more specific with question. Nobody knows what IDE you are using, except yourself.

---

