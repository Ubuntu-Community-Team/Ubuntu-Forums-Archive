---
title: "Spotify Will Not Start"
date: 2012-07-16
forum: New to Ubuntu
---

### Post by MrGreenGenes on 2012-07-16
Hi,

I'm new to Linux, getting my head around a lot of things but stuck with trying to get Spotify to work. I keep getting this message when I try from the terminal:


Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
06:53:40.208 I [breakpad.cpp:62                 ] Registered Breakpad for product: spotify

06:53:40.208 I [translate.cpp:123               ] Reloading language file
06:53:40.209 I [breakpad.cpp:192                ] Searching for crashdumps: /home/jon/.cache/spotify/*.dmp

Any help would be much appreciated!

Cheers :)

---

### Post by Daveth on 2012-07-16
you trying Spotify for Linux, or Windows Spotify under Wine?

---

### Post by jakerella on 2012-07-25
FYI, I have this issue as well, below is the full dump from the command line when starting spotify. Note that this began happening about a week ago, and without any updates being performed (to Spotify or anything else, I run the Update Manager weekly, and this issue began in between updates).

This is the spotify for linux app, not running under wine:

```
~$ spotify 
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
14:12:41.542 I [breakpad.cpp:61                 ] Registered Breakpad for product: spotify

14:12:41.543 I [translate.cpp:123               ] Reloading language file
14:12:41.544 I [breakpad.cpp:191                ] Searching for crashdumps: /home/jordan/.cache/spotify/*.dmp

14:12:52.697 I [breakpad.cpp:202                ] Not allowed to upload file

14:12:52.766 A [CefModule.cpp:325               ] Check failed: g_cef_handle: 
14:12:53.170 I [ap:1755                         ] Connecting to AP E5.spotify.com:4070
14:12:53.187 I [mainview:967                    ] Registering bundled framework import with version 0.1.0
14:12:53.187 I [mainview:964                    ] Registering bundled app html with version 0.1.0
14:12:53.187 I [mainview:967                    ] Registering bundled framework bridge-desktop with version 0.2.0
14:12:53.187 I [mainview:967                    ] Registering bundled framework api with version 0.1.0
14:12:53.187 I [mainview:967                    ] Registering bundled framework resources with version 0.2.0
14:12:53.187 I [mainview:967                    ] Registering bundled framework unstable with version 0.2.0
14:12:53.187 I [mainview:967                    ] Registering bundled framework util with version 0.1.0
14:12:53.187 I [mainview:964                    ] Registering bundled app album-header with version 1.0.0
14:12:53.187 I [mainview:964                    ] Registering bundled app bundles with version 1.0.0
14:12:53.187 I [mainview:964                    ] Registering bundled app error with version 1.0.0
14:12:53.187 I [mainview:964                    ] Registering bundled app feed with version 1.0.0
14:12:53.187 I [mainview:964                    ] Registering bundled app finder with version 1.0.0
14:12:53.187 I [mainview:964                    ] Registering bundled app home with version 1.0.0
14:12:53.187 I [mainview:964                    ] Registering bundled app install with version 1.0.0
14:12:53.187 I [mainview:964                    ] Registering bundled app people with version 1.0.0
14:12:53.187 I [mainview:964                    ] Registering bundled app profile with version 1.0.3
14:12:53.187 I [mainview:964                    ] Registering bundled app profile-header with version 1.0.3
14:12:53.187 I [mainview:964                    ] Registering bundled app radio with version 1.0.0
14:12:53.187 I [mainview:964                    ] Registering bundled app search-dropdown with version 1.0.1
14:12:53.187 I [mainview:964                    ] Registering bundled app search-header with version 1.0.0
14:12:53.187 I [mainview:964                    ] Registering bundled app share with version 1.0.0
14:12:53.187 I [mainview:964                    ] Registering bundled app subscribe-popup with version 0.2.2
14:12:53.187 I [mainview:964                    ] Registering bundled app og-popup with version 1.0.0
14:12:53.189 I [AppBundle.cpp:75                ] Loaded bundle for bridge-desktop.
14:12:53.189 I [AppBundle.cpp:75                ] Loaded bundle for People.
14:12:53.189 I [AppBundle.cpp:75                ] Loaded bundle for People.
14:12:53.191 I [AppBundle.cpp:75                ] Loaded bundle for App Finder.
14:12:53.193 I [AppBundle.cpp:75                ] Loaded bundle for App Finder.
14:12:53.194 I [AppBundle.cpp:75                ] Loaded bundle for Radio.
14:12:53.194 I [AppBundle.cpp:75                ] Loaded bundle for Radio.
14:12:53.244 I [AppBundle.cpp:75                ] Loaded bundle for Feed.
14:12:53.246 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:53.246 I [AppBundle.cpp:75                ] Loaded bundle for bridge-desktop.
14:12:53.252 I [AppBundle.cpp:75                ] Loaded bundle for resources.
14:12:53.252 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:53.254 I [AppBundle.cpp:75                ] Loaded bundle for unstable.
14:12:53.254 I [AppBundle.cpp:75                ] Loaded bundle for import.
14:12:53.254 I [AppManager.cpp:147              ] Created instance of the application feed.
14:12:53.255 I [AppBundle.cpp:75                ] Loaded bundle for search-dropdown.
14:12:53.260 I [AppBundle.cpp:75                ] Loaded bundle for resources.
14:12:53.262 I [AppBundle.cpp:75                ] Loaded bundle for unstable.
14:12:53.263 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:53.263 I [AppBundle.cpp:75                ] Loaded bundle for bridge-desktop.
14:12:53.263 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:53.264 I [AppBundle.cpp:75                ] Loaded bundle for import.
14:12:53.264 I [AppManager.cpp:147              ] Created instance of the application search-dropdown.
14:12:53.266 I [AppBundle.cpp:75                ] Loaded bundle for What's New.
14:12:53.268 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:53.268 I [AppBundle.cpp:75                ] Loaded bundle for bridge-desktop.
14:12:53.273 I [AppBundle.cpp:75                ] Loaded bundle for resources.
14:12:53.273 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:53.275 I [AppBundle.cpp:75                ] Loaded bundle for unstable.
14:12:53.275 I [AppBundle.cpp:75                ] Loaded bundle for import.
14:12:53.276 I [AppManager.cpp:147              ] Created instance of the application home.
14:12:53.281 I [AppManager.cpp:189              ] Keeping application What's New alive for 60000 ms.
14:12:53.282 I [offline-mgr:2084                ] Storage has been cleaned
14:12:53.308 I [AppBundle.cpp:75                ] Loaded bundle for Feed.
14:12:53.309 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:53.310 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:53.310 I [AppBundle.cpp:75                ] Loaded bundle for album-header.
14:12:53.311 I [AppBundle.cpp:75                ] Loaded bundle for Open Graph popup.
14:12:53.312 I [AppBundle.cpp:75                ] Loaded bundle for Search Header.
14:12:53.312 I [AppBundle.cpp:75                ] Loaded bundle for search-dropdown.
14:12:53.313 I [AppBundle.cpp:75                ] Loaded bundle for Share.
14:12:53.315 I [AppBundle.cpp:75                ] Loaded bundle for App Finder.
14:12:53.321 I [AppBundle.cpp:75                ] Loaded bundle for resources.
14:12:53.322 I [AppBundle.cpp:75                ] Loaded bundle for Subscribe popup.
14:12:53.324 I [AppBundle.cpp:75                ] Loaded bundle for unstable.
14:12:53.326 I [AppBundle.cpp:75                ] Loaded bundle for What's New.
14:12:53.327 I [AppBundle.cpp:75                ] Loaded bundle for What's New.
14:12:53.327 I [AppBundle.cpp:75                ] Loaded bundle for profile-header.
14:12:53.327 I [AppBundle.cpp:75                ] Loaded bundle for search-header.
14:12:53.327 I [AppBundle.cpp:75                ] Loaded bundle for bridge-desktop.
14:12:53.327 I [AppBundle.cpp:75                ] Loaded bundle for install.
14:12:53.327 I [AppBundle.cpp:75                ] Loaded bundle for Bundles.
14:12:53.327 I [AppBundle.cpp:75                ] Loaded bundle for profile.
14:12:53.327 I [AppBundle.cpp:75                ] Loaded bundle for People.
14:12:53.327 I [AppBundle.cpp:75                ] Loaded bundle for Share.
14:12:53.333 I [AppBundle.cpp:75                ] Loaded bundle for resources.
14:12:53.333 I [AppBundle.cpp:75                ] Loaded bundle for error.
14:12:53.333 I [AppBundle.cpp:75                ] Loaded bundle for HTML5 Test.
14:12:53.334 I [AppBundle.cpp:75                ] Loaded bundle for Feed.
14:12:53.334 I [AppBundle.cpp:75                ] Loaded bundle for unstable.
14:12:53.334 I [AppBundle.cpp:75                ] Loaded bundle for search-dropdown.
14:12:53.334 I [AppBundle.cpp:75                ] Loaded bundle for album-header.
14:12:53.334 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:53.336 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:53.336 I [AppBundle.cpp:75                ] Loaded bundle for import.
14:12:53.337 I [AppBundle.cpp:75                ] Loaded bundle for Open Graph popup.
14:12:53.337 I [AppBundle.cpp:75                ] Loaded bundle for Subscribe popup.
14:12:53.337 I [AppBundle.cpp:75                ] Loaded bundle for Radio.
14:12:53.337 I [AppBundle.cpp:75                ] Loaded bundle for App Finder.
14:12:53.368 I [ap:1229                         ] Connected to AP: 193.182.8.54:4070
14:12:53.371 I [mainview:6209                   ] onAppActivate(1)
14:12:53.460 I [mainview:6768                   ] Load complete (0) url: sp://feed/index.html
14:12:53.488 I [mainview:6768                   ] Load complete (0) url: sp://home/index.html
14:12:53.768 I [gui-model:2846                  ] Login Code: 0
14:12:53.769 I [AppBundle.cpp:75                ] Loaded bundle for album-header.
14:12:53.770 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:53.770 I [AppBundle.cpp:75                ] Loaded bundle for bridge-desktop.
14:12:53.777 I [AppBundle.cpp:75                ] Loaded bundle for resources.
14:12:53.777 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:53.778 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:53.778 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:53.779 I [AppBundle.cpp:75                ] Loaded bundle for search-dropdown.
14:12:53.785 I [AppBundle.cpp:75                ] Loaded bundle for resources.
14:12:53.786 I [AppBundle.cpp:75                ] Loaded bundle for unstable.
14:12:53.787 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:53.787 I [AppBundle.cpp:75                ] Loaded bundle for bridge-desktop.
14:12:53.788 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:53.788 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:53.789 I [AppBundle.cpp:75                ] Loaded bundle for Search Header.
14:12:53.794 I [AppBundle.cpp:75                ] Loaded bundle for resources.
14:12:53.796 I [AppBundle.cpp:75                ] Loaded bundle for unstable.
14:12:53.797 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:53.797 I [AppBundle.cpp:75                ] Loaded bundle for bridge-desktop.
14:12:53.797 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:53.797 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:53.889 I [AppBundle.cpp:75                ] Loaded bundle for App Finder.
14:12:53.891 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:53.891 I [AppBundle.cpp:75                ] Loaded bundle for bridge-desktop.
14:12:53.896 I [AppBundle.cpp:75                ] Loaded bundle for resources.
14:12:53.896 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:53.897 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:53.897 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:53.899 I [AppBundle.cpp:75                ] Loaded bundle for Share.
14:12:53.900 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:53.900 I [AppBundle.cpp:75                ] Loaded bundle for bridge-desktop.
14:12:53.906 I [AppBundle.cpp:75                ] Loaded bundle for resources.
14:12:53.906 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:53.908 I [AppBundle.cpp:75                ] Loaded bundle for unstable.
14:12:53.909 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:53.912 I [AppBundle.cpp:75                ] Loaded bundle for What's New.
14:12:53.913 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:53.913 I [AppBundle.cpp:75                ] Loaded bundle for bridge-desktop.
14:12:53.918 I [AppBundle.cpp:75                ] Loaded bundle for resources.
14:12:53.919 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:53.920 I [AppBundle.cpp:75                ] Loaded bundle for unstable.
14:12:53.922 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:53.922 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:53.923 I [AppBundle.cpp:75                ] Loaded bundle for Open Graph popup.
14:12:53.924 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:53.924 I [AppBundle.cpp:75                ] Loaded bundle for bridge-desktop.
14:12:53.929 I [AppBundle.cpp:75                ] Loaded bundle for resources.
14:12:53.930 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:53.931 I [AppBundle.cpp:75                ] Loaded bundle for unstable.
14:12:53.933 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:53.938 I [AppBundle.cpp:75                ] Loaded bundle for resources.
14:12:53.938 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:53.939 I [AppBundle.cpp:75                ] Loaded bundle for Subscribe popup.
14:12:53.940 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:53.940 I [AppBundle.cpp:75                ] Loaded bundle for bridge-desktop.
14:12:53.945 I [AppBundle.cpp:75                ] Loaded bundle for resources.
14:12:53.946 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:53.947 I [AppBundle.cpp:75                ] Loaded bundle for unstable.
14:12:53.948 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:53.954 I [AppBundle.cpp:75                ] Loaded bundle for resources.
14:12:53.954 I [AppBundle.cpp:75                ] Loaded bundle for unstable.
14:12:53.954 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:53.956 I [AppBundle.cpp:75                ] Loaded bundle for unstable.
14:12:53.957 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:53.957 I [AppBundle.cpp:75                ] Loaded bundle for bridge-desktop.
14:12:53.963 I [AppBundle.cpp:75                ] Loaded bundle for resources.
14:12:53.963 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:53.964 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:53.970 I [AppBundle.cpp:75                ] Loaded bundle for resources.
14:12:53.970 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:53.971 I [AppBundle.cpp:75                ] Loaded bundle for Feed.
14:12:53.972 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:53.972 I [AppBundle.cpp:75                ] Loaded bundle for bridge-desktop.
14:12:53.977 I [AppBundle.cpp:75                ] Loaded bundle for resources.
14:12:53.978 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:53.979 I [AppBundle.cpp:75                ] Loaded bundle for unstable.
14:12:53.981 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:53.981 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:53.986 I [AppBundle.cpp:75                ] Loaded bundle for resources.
14:12:53.988 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:53.988 I [AppBundle.cpp:75                ] Loaded bundle for bridge-desktop.
14:12:53.993 I [AppBundle.cpp:75                ] Loaded bundle for resources.
14:12:53.993 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:53.994 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:53.994 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:53.995 I [AppBundle.cpp:75                ] Loaded bundle for Subscribe popup.
14:12:53.996 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:53.996 I [AppBundle.cpp:75                ] Loaded bundle for bridge-desktop.
14:12:54.001 I [AppBundle.cpp:75                ] Loaded bundle for resources.
14:12:54.002 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:54.003 I [AppBundle.cpp:75                ] Loaded bundle for unstable.
14:12:54.004 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:54.006 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:54.006 I [AppBundle.cpp:75                ] Loaded bundle for bridge-desktop.
14:12:54.011 I [AppBundle.cpp:75                ] Loaded bundle for resources.
14:12:54.012 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:54.012 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:54.023 I [AppBundle.cpp:75                ] Loaded bundle for resources.
14:12:54.024 I [AppBundle.cpp:75                ] Loaded bundle for unstable.
14:12:54.024 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:54.025 I [AppBundle.cpp:75                ] Loaded bundle for Open Graph popup.
14:12:54.026 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:54.026 I [AppBundle.cpp:75                ] Loaded bundle for bridge-desktop.
14:12:54.031 I [AppBundle.cpp:75                ] Loaded bundle for resources.
14:12:54.031 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:54.033 I [AppBundle.cpp:75                ] Loaded bundle for unstable.
14:12:54.034 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:54.035 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:54.035 I [AppBundle.cpp:75                ] Loaded bundle for bridge-desktop.
14:12:54.041 I [AppBundle.cpp:75                ] Loaded bundle for resources.
14:12:54.041 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:54.041 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:54.048 I [AppBundle.cpp:75                ] Loaded bundle for resources.
14:12:54.048 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:54.169 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:54.174 I [AppBundle.cpp:75                ] Loaded bundle for resources.
14:12:54.176 I [AppBundle.cpp:75                ] Loaded bundle for unstable.
14:12:54.177 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:54.177 I [AppBundle.cpp:75                ] Loaded bundle for bridge-desktop.
14:12:54.182 I [AppBundle.cpp:75                ] Loaded bundle for resources.
14:12:54.183 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:54.184 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:54.185 I [AppBundle.cpp:75                ] Loaded bundle for api.
14:12:54.185 I [AppBundle.cpp:75                ] Loaded bundle for bridge-desktop.
14:12:54.190 I [AppBundle.cpp:75                ] Loaded bundle for resources.
14:12:54.190 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:54.191 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:54.196 I [AppBundle.cpp:75                ] Loaded bundle for resources.
14:12:54.196 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:54.222 I [mainview:6768                   ] Load complete (0) url: sp://home/index.html
14:12:54.378 I [AppBundle.cpp:75                ] Loaded bundle for util.
14:12:54.870 I [AppBundle.cpp:75                ] Loaded bundle for resources.
[0725/091255:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0725/091255:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0725/091255:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0725/091255:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0725/091255:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
14:12:55.722 I [ad:1040                         ] Found ad (time = 1343225575, adclass = 'mpu', time left = 0, length = 86400)
[0725/091255:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0725/091256:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0725/091256:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0725/091256:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0725/091256:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
14:12:56.160 I [ad:1040                         ] Found ad (time = 0, adclass = '', time left = 30, length = 30)
Segmentation fault
```

Edit: I have since run all updates in the Update Manager, FYI, but Spotify will still not start (same result).

---

### Post by jakerella on 2012-07-25
Did a little more poking around online and found that removing the .cache/spotify folder entirely will allow Spotify for linux to start up again.

However, some people are saying that the new version (0.8.4.101...) has fixed this issue. When I tried updating it said the signature for the spotify deb source couldn't be verified.

Solution: redo your key verification and update Spotify
([https://www.spotify.com/us/download/previews/](https://www.spotify.com/us/download/previews/))

If you continue to have problems, the work around is to remove that .cache/spotify directory each time before starting Spotify for linux.

---

### Post by pererik87 on 2012-07-28
This works. Probably there is some bug here. I am not interesting in knowing what happened, but i hope this is resolved sometime in history. I <3 spotify Anyways. If this post i burried in replies in ubuntu. home folde-> wiev-> show hidden files-> .cache -> remove spotify folder. I think this bug is cause by exiting while spotfy commerical is played. i respect commericals but when i shutdown the computer that is priotiry 1. to finshing spotify commericals. sorry spotify guys.. i <3 even thou u can be stupid at certain times. <3 <3

---

