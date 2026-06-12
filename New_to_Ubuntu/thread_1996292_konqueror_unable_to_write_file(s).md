---
title: "konqueror unable to write file(s)"
date: 2012-06-04
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2012-06-04
Hi all
i've just installed Konqueror as a test browser. 
When I open Konqueror I get a bunch of error messages saying that certain files in the ~/.kde/share/config directory are not writeable. Please contact the systems admin.

Ok, I chown all the files in that directory from root:root to glenn:glenn:

```

glenn@design:~/.kde/share/config$ ls -al
total 84
drwxr-xr-x 2 root root 4096 Jun  4 21:31 .
drwxr-xr-x 5 root root 4096 Jun  4 21:28 ..
-rw------- 1 root root  570 Jun  4 21:28 filetypesrc
-rw------- 1 root root   67 Jun  4 21:28 katerc
-rw------- 1 root root  464 Jun  4 21:28 kcmnspluginrc
-rw------- 1 root root  862 Jun  4 21:28 kconf_updaterc
-rw------- 1 root root   76 Jun  4 21:28 kcookiejarrc
-rw------- 1 root root  240 Jun  4 21:31 kdebugrc
-rw------- 1 root root   39 Jun  4 21:28 kdedrc
-rw------- 1 root root   39 Jun  4 21:28 kdeglobals
-rw------- 1 root root   55 Jun  4 21:28 kfmclientrc
-rw------- 1 root root   69 Jun  4 21:28 kio_httprc
-rw------- 1 root root  110 Jun  4 21:30 kioslaverc
-rw------- 1 root root   33 Jun  4 21:31 konq_history
-rw------- 1 root root  136 Jun  4 21:31 konquerorrc
-rw------- 1 root root  122 Jun  4 21:29 ktimezonedrc
-rw------- 1 root root   58 Jun  4 21:28 kuriikwsfilterrc
-rw------- 1 root root   85 Jun  4 21:28 nepomukserverrc
-rw------- 1 root root   22 Jun  4 21:28 phonondevicesrc
-rw-r--r-- 1 root root  143 Jun  2 11:55 profilerc
-rw------- 1 root root  634 Jun  4 21:30 rekonqrc
glenn@design:~/.kde/share/config$ sudo chown glenn:glenn *

drwxr-xr-x 2 root  root  4096 Jun  4 21:31 .
drwxr-xr-x 5 root  root  4096 Jun  4 21:28 ..
-rw------- 1 glenn glenn  570 Jun  4 21:28 filetypesrc
-rw------- 1 glenn glenn   67 Jun  4 21:28 katerc
-rw------- 1 glenn glenn  464 Jun  4 21:28 kcmnspluginrc
-rw------- 1 glenn glenn  862 Jun  4 21:28 kconf_updaterc
-rw------- 1 glenn glenn   76 Jun  4 21:28 kcookiejarrc
-rw------- 1 glenn glenn  240 Jun  4 21:31 kdebugrc
-rw------- 1 glenn glenn   39 Jun  4 21:28 kdedrc
-rw------- 1 glenn glenn   39 Jun  4 21:28 kdeglobals
-rw------- 1 glenn glenn   55 Jun  4 21:28 kfmclientrc
-rw------- 1 glenn glenn   69 Jun  4 21:28 kio_httprc
-rw------- 1 glenn glenn  110 Jun  4 21:30 kioslaverc
-rw------- 1 glenn glenn   33 Jun  4 21:31 konq_history
-rw------- 1 glenn glenn  136 Jun  4 21:31 konquerorrc
-rw------- 1 glenn glenn  122 Jun  4 21:29 ktimezonedrc
-rw------- 1 glenn glenn   58 Jun  4 21:28 kuriikwsfilterrc
-rw------- 1 glenn glenn   85 Jun  4 21:28 nepomukserverrc
-rw------- 1 glenn glenn   22 Jun  4 21:28 phonondevicesrc
-rw-r--r-- 1 glenn glenn  143 Jun  2 11:55 profilerc
-rw------- 1 glenn glenn  634 Jun  4 21:30 rekonqrc
glenn@design:~/.kde/share/config$

```But when i launch Konqueror I still get that error message...?
I cant get Konqueror to launch from the menu icon, only from the command line. And when i do i get this:
```

glenn@design:~$ konqueror
couldn't lock local file 
konqueror(7175)/KSharedDataCache KSharedDataCache::Private::mapSharedMemory: Failed to establish shared memory mapping, will fallback to private memory -- memory usage will increase 
trying to create local folder /home/glenn/.kde/share/apps/konqueror: Permission denied
trying to create local folder /home/glenn/.kde/share/apps/konqueror: Permission denied
QFile::remove: Empty or null file name
kdeinit4: Aborting. bind() failed: Permission denied
Could not bind to socket '/home/glenn/.kde/socket-design/kdeinit4__0'
trying to create local folder /home/glenn/.kde/share/kde4/services: Permission denied
konqueror(7175): No ksycoca4 database available! 

konqueror(7175)/kdecore (trader) KServiceTypeTrader::defaultOffers: KServiceTypeTrader: serviceType  "Browser/View"  not found 
trying to create local folder /home/glenn/.kde/share/apps/konqueror: Permission denied
trying to create local folder /home/glenn/.kde/share/apps/konqueror: Permission denied
trying to create local folder /home/glenn/.kde/share/apps/konqueror: Permission denied
trying to create local folder /home/glenn/.kde/tmp-design/closeditems: Permission denied
konqueror(7175): No ksycoca4 database available! 

konqueror(7175)/kdecore (trader) KServiceTypeTrader::defaultOffers: KServiceTypeTrader: serviceType  "KonqAboutPage"  not found 
konqueror(7175) KonqFactory::createView: no part was associated with "KonqAboutPage" 
konqueror(7175) KonqViewManager::loadItem: Profile Loading Error: View creation failed 
trying to create local folder /home/glenn/.kde/share/apps/konqueror: Permission denied
QFile::remove: Empty or null file name
QFile::remove: Empty or null file name
QFile::remove: Empty or null file name
QFile::remove: Empty or null file name
kdeinit4: Aborting. bind() failed: Permission denied
Could not bind to socket '/home/glenn/.kde/socket-design/kdeinit4__0'
trying to create local folder /home/glenn/.kde/share/kde4/services: Permission denied
konqueror(7175): No ksycoca4 database available! 

konqueror(7175): No ksycoca4 database available! 

konqueror(7175): No ksycoca4 database available! 

konqueror(7175): No ksycoca4 database available! 

konqueror(7175): No ksycoca4 database available! 

konqueror(7175): No ksycoca4 database available! 

konqueror(7175): No ksycoca4 database available! 

konqueror(7175): No ksycoca4 database available! 

konqueror(7175): No ksycoca4 database available! 

konqueror(7175): No ksycoca4 database available! 

konqueror(7175): No ksycoca4 database available! 

QFile::remove: Empty or null file name
kdeinit4: Aborting. bind() failed: Permission denied
Could not bind to socket '/home/glenn/.kde/socket-design/kdeinit4__0'
trying to create local folder /home/glenn/.kde/share/kde4/services: Permission denied
konqueror(7175): No ksycoca4 database available! 

konqueror(7175)/kdecore (trader) KServiceTypeTrader::defaultOffers: KServiceTypeTrader: serviceType  "KUriFilter/Plugin"  not found 
QFile::remove: Empty or null file name
kdeinit4: Aborting. bind() failed: Permission denied
Could not bind to socket '/home/glenn/.kde/socket-design/kdeinit4__0'
trying to create local folder /home/glenn/.kde/share/kde4/services: Permission denied
konqueror(7175): No ksycoca4 database available! 

konqueror(7175): No ksycoca4 database available! 

QFile::remove: Empty or null file name
kdeinit4: Aborting. bind() failed: Permission denied
Could not bind to socket '/home/glenn/.kde/socket-design/kdeinit4__0'
trying to create local folder /home/glenn/.kde/share/kde4/services: Permission denied
konqueror(7175): No ksycoca4 database available! 

konqueror(7175)/kdecore (trader) mimeTypeSycocaOffers: KMimeTypeTrader: mimeType "text/html" not found 
QFile::remove: Empty or null file name
kdeinit4: Aborting. bind() failed: Permission denied
Could not bind to socket '/home/glenn/.kde/socket-design/kdeinit4__0'
trying to create local folder /home/glenn/.kde/share/kde4/services: Permission denied
konqueror(7175): No ksycoca4 database available! 

konqueror(7175)/kdecore (trader): KMimeTypeTrader: couldn't find service type "Application" 
Please ensure that the .desktop file for it is installed; then run kbuildsycoca4. 
QFile::remove: Empty or null file name
kdeinit4: Aborting. bind() failed: Permission denied
Could not bind to socket '/home/glenn/.kde/socket-design/kdeinit4__0'
trying to create local folder /home/glenn/.kde/share/kde4/services: Permission denied
konqueror(7175): No ksycoca4 database available! 

konqueror(7175): No ksycoca4 database available! 

QFile::remove: Empty or null file name
kdeinit4: Aborting. bind() failed: Permission denied
Could not bind to socket '/home/glenn/.kde/socket-design/kdeinit4__0'
trying to create local folder /home/glenn/.kde/share/kde4/services: Permission denied
konqueror(7175): No ksycoca4 database available! 

konqueror(7175)/kdecore (trader) mimeTypeSycocaServiceOffers: KMimeTypeTrader: mimeType "text/html" not found 
QFile::remove: Empty or null file name
kdeinit4: Aborting. bind() failed: Permission denied
Could not bind to socket '/home/glenn/.kde/socket-design/kdeinit4__0'
trying to create local folder /home/glenn/.kde/share/kde4/services: Permission denied
konqueror(7175): No ksycoca4 database available! 

konqueror(7175)/kdecore (trader): KMimeTypeTrader: couldn't find service type "Application" 
Please ensure that the .desktop file for it is installed; then run kbuildsycoca4. 
QFile::remove: Empty or null file name
kdeinit4: Aborting. bind() failed: Permission denied
Could not bind to socket '/home/glenn/.kde/socket-design/kdeinit4__0'
trying to create local folder /home/glenn/.kde/share/kde4/services: Permission denied
konqueror(7175): No ksycoca4 database available! 

konqueror(7175)/kdecore (trader) mimeTypeSycocaServiceOffers: KMimeTypeTrader: mimeType "text/html" not found 
QFile::remove: Empty or null file name
kdeinit4: Aborting. bind() failed: Permission denied
Could not bind to socket '/home/glenn/.kde/socket-design/kdeinit4__0'
trying to create local folder /home/glenn/.kde/share/kde4/services: Permission denied
konqueror(7175): No ksycoca4 database available! 

konqueror(7175)/kdecore (trader): KMimeTypeTrader: couldn't find service type "KParts/ReadOnlyPart" 
Please ensure that the .desktop file for it is installed; then run kbuildsycoca4. 
konqueror(7175) KonqFactory::createView: no part was associated with "text/html" 
QFile::remove: Empty or null file name
kdeinit4: Aborting. bind() failed: Permission denied
Could not bind to socket '/home/glenn/.kde/socket-design/kdeinit4__0'
trying to create local folder /home/glenn/.kde/share/kde4/services: Permission denied
konqueror(7175): No ksycoca4 database available! 

konqueror(7175): No ksycoca4 database available! 

QFile::remove: Empty or null file name
kdeinit4: Aborting. bind() failed: Permission denied
Could not bind to socket '/home/glenn/.kde/socket-design/kdeinit4__0'
trying to create local folder /home/glenn/.kde/share/kde4/services: Permission denied
konqueror(7175): No ksycoca4 database available! 

QFile::remove: Empty or null file name
kdeinit4: Aborting. bind() failed: Permission denied
Could not bind to socket '/home/glenn/.kde/socket-design/kdeinit4__0'
trying to create local folder /home/glenn/.kde/share/kde4/services: Permission denied
konqueror(7175): No ksycoca4 database available! 

konqueror(7175)/kdecore (trader): KMimeTypeTrader: couldn't find service type "Application" 
Please ensure that the .desktop file for it is installed; then run kbuildsycoca4. 
QFile::remove: Empty or null file name
kdeinit4: Aborting. bind() failed: Permission denied
Could not bind to socket '/home/glenn/.kde/socket-design/kdeinit4__0'
trying to create local folder /home/glenn/.kde/share/kde4/services: Permission denied
konqueror(7175): No ksycoca4 database available! 

konqueror(7175)/kdecore (trader) mimeTypeSycocaServiceOffers: KMimeTypeTrader: mimeType "text/html" not found 
QFile::remove: Empty or null file name
kdeinit4: Aborting. bind() failed: Permission denied
Could not bind to socket '/home/glenn/.kde/socket-design/kdeinit4__0'
trying to create local folder /home/glenn/.kde/share/kde4/services: Permission denied
konqueror(7175): No ksycoca4 database available! 

konqueror(7175)/kdecore (trader): KMimeTypeTrader: couldn't find service type "Application" 
Please ensure that the .desktop file for it is installed; then run kbuildsycoca4. 
QFile::remove: Empty or null file name
QFile::remove: Empty or null file name
kdeinit4: Aborting. bind() failed: Permission denied
Could not bind to socket '/home/glenn/.kde/socket-design/kdeinit4__0'
trying to create local folder /home/glenn/.kde/share/kde4/services: Permission denied
konqueror(7175): No ksycoca4 database available! 

konqueror(7175): No ksycoca4 database available! 

QFile::remove: Empty or null file name
kdeinit4: Aborting. bind() failed: Permission denied
Could not bind to socket '/home/glenn/.kde/socket-design/kdeinit4__0'
trying to create local folder /home/glenn/.kde/share/kde4/services: Permission denied
KCrash: Application 'konqueror' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/glenn/.kde/socket-design/kdeinit4__0
Warning: connect() failed: : Permission denied
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi directly
couldn't lock local file 
drkonqi(7231)/KSharedDataCache KSharedDataCache::Private::mapSharedMemory: Failed to establish shared memory mapping, will fallback to private memory -- memory usage will increase 
couldn't lock local file 
kdialog(7236)/KSharedDataCache KSharedDataCache::Private::mapSharedMemory: Failed to establish shared memory mapping, will fallback to private memory -- memory usage will increase 
couldn't lock local file 

[1]+  Stopped                 konqueror
glenn@design:~$ QFile::remove: Empty or null file name
kdeinit4: Aborting. bind() failed: Permission denied
Could not bind to socket '/home/glenn/.kde/socket-design/kdeinit4__0'
couldn't lock local file 
drkonqi(7231): "KLauncher could not be reached via D-Bus. Error when calling kdeinit_exec:
The name org.kde.klauncher was not provided by any .service files
" 

```Is any of this desipherable...But when I open Konqueror as SU I only get:

```

glenn@design:~$ sudo konqueror
[sudo] password for glenn: 
konqueror(7342)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "libkhtmlpart.so"

```

Why do I have to open Konqueror as SU? I don't have to with any other of my programs?

---

### Post by inashdeen on 2012-06-04
how do you install the browser? compile or sudo apt-get install?

---

### Post by Senior_Buckethead on 2012-06-04
using apt, just like every other piece of software I have.

---

### Post by Senior_Buckethead on 2012-06-07
Bump

---

### Post by steeldriver on 2012-06-07
look at your 'ls' output again - root also owns (at least) the parent and grandparent dirs (~/.kde/share/config and ~/.kde/share)

```

drwxr-xr-x 2 root  root  4096 Jun  4 21:31 . 
drwxr-xr-x 5 root  root  4096 Jun  4 21:28 ..

```you need to go up at least to ~/.kde I think, and do a chown -R glenn:glenn (I would go up to ~ and do chown -R glenn:glenn .kde)

and I'd recommend NOT doing sudo konqueror - that's possibly what got you in this mess

---

### Post by Senior_Buckethead on 2012-06-08
Thank you.

I sudo chmod -R glenn:glenn .kde and everything in it. It runs from prompt but still gives out loads of message at the prompt. So many that when I scroll back I cant get to the beginning.

I try to not run apps via. sudo because i know thats not a safe thing to do, I was only illustrating here that it was the only way to even make it go, it wouldnt run from normal user and wouldnt run from menu.

---

