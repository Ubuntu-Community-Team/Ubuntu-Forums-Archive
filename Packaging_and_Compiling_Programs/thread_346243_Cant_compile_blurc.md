---
title: "Cant compile blurc"
date: 2007-01-25
forum: Packaging and Compiling Programs
---

### Post by christhemonkey on 2007-01-25
When trying to compile blurc-0.1b (from here [http://blurc.sourceforge.net/](http://blurc.sourceforge.net/))
I get this error:

```
chris@chris-desktop:~/blurc-0.1b$ make
g++ -O2 -c UuidHandler.cpp
UuidHandler.cpp: In static member function `static uint128_t* 
   UuidHandler::create_base_uuid()':
UuidHandler.cpp:64: error: cannot convert `uint128_t*' to `char*' in assignment
make: *** [UuidHandler.o] Error 1

```


The relevant bit of code (i think, dont know C++) is this:

```
uint128_t* UuidHandler::create_base_uuid()
{
        char baseStr[128];
        int delim = '-';
        unsigned long dataLongValue;
        char *delimPtr;
        char *dataPtr;
        char temp[10];
        int toBeCopied;
        char *data;

        if (uuid_data == NULL) {
                strcpy(baseStr, UUID);
                uuid_data = (uint128_t *)malloc(sizeof(uint128_t));
                data = uuid_data->data;
                memset(data, '\0', sizeof(uint128_t));
                memset(temp, '\0', 10);
                dataPtr = baseStr;
                delimPtr = NULL;
                delimPtr = strchr(dataPtr, delim);
                toBeCopied = delimPtr - dataPtr;
                if (toBeCopied != 8) {
                        return NULL;
                }
                strncpy(temp, dataPtr, toBeCopied);
                dataLongValue = htonl(strtoul(temp, NULL, 16));
                memcpy(&data[0], &dataLongValue, 4);

                /*
                 * Get the next 4 bytes (note that there is a "-"
                 * between them now)
                 */
                memset(temp, '\0', 10);
                dataPtr = delimPtr + 1;
                delimPtr = strchr(dataPtr, delim);
                toBeCopied = delimPtr - dataPtr;
                if (toBeCopied != 4) {
                        return NULL;
                }
                strncpy(temp, dataPtr, toBeCopied);
                dataPtr = delimPtr + 1;
                delimPtr = strchr(dataPtr, delim);
                toBeCopied = delimPtr - dataPtr;
                if (toBeCopied != 4) {
                        return NULL;
                }
                strncat(temp, dataPtr, toBeCopied);
                dataLongValue = htonl(strtoul(temp, NULL, 16));
                memcpy(&data[4], &dataLongValue, 4);

                /*
                 * Get the last 4 bytes (note that there are 6 bytes
                 * after the last separator, which is truncated (2+4)
                 */
                memset(temp, '\0', 10);
                dataPtr = delimPtr + 1;
                dataPtr = delimPtr + 1;
                delimPtr = strchr(dataPtr, delim);
                toBeCopied = delimPtr - dataPtr;
                if (toBeCopied != 4) {
                        return NULL;
                }
                strncpy(temp, dataPtr, toBeCopied);
                strncat(temp, (delimPtr + 1), 4);
                dataLongValue = htonl(strtoul(temp, NULL, 16));
                memcpy(&data[8], &dataLongValue, 4);
                dataLongValue = htonl(strtoul(delimPtr + 5, NULL, 16));
                memcpy(&data[12], &dataLongValue, 4);
        }
        return uuid_data;
}


```


Some help wold really be appreciated as i would love to get this working.
Cheers, Chris

---

### Post by christhemonkey on 2007-01-25
Ok just to say i found a patch that fixes this.

For the curious its here:
[http://aur.archlinux.org/packages/blurc/blurc/blurc.patch](http://aur.archlinux.org/packages/blurc/blurc/blurc.patch)


Basically just add a (char *) to line 64.

---

### Post by [S2] on 2008-01-09
> **christhemonkey said:**
> Ok just to say i found a patch that fixes this.

For the curious its here:
[http://aur.archlinux.org/packages/blurc/blurc/blurc.patch](http://aur.archlinux.org/packages/blurc/blurc/blurc.patch)


Basically just add a (char *) to line 64.

Thanks! I quote it here for convenience:
```
--- UuidHandler.cpp	2005-12-08 16:54:43.000000000 +0100
+++ UuidHandler.cpp.ok  2005-12-08 16:36:54.000000000 +0100
@@ -61,7 +61,7 @@
         if (uuid_data == NULL) {
                 strcpy(baseStr, UUID);
                 uuid_data = (uint128_t *)malloc(sizeof(uint128_t));
-                data = uuid_data->data;
+                data = (char *)uuid_data->data;
                 memset(data, '\0', sizeof(uint128_t));
                 memset(temp, '\0', 10);
                 dataPtr = baseStr;
--- Makefile	2005-02-04 13:53:20.000000000 +0100
+++ Makefile.ok	2005-12-08 17:40:59.000000000 +0100
@@ -11,9 +11,9 @@
 SHELL = /bin/sh
 LIB = -lpthread -lbluetooth
 OPTS = -O2
-BLURCD_CONFIG_DIR = /etc/blurcd
-BLURCD_BIN_DIR = /usr/sbin
-BLURCD_SHARE_DIR = /usr/share/blurc
+BLURCD_CONFIG_DIR = ${DESTDIR}/etc/blurcd
+BLURCD_BIN_DIR = ${DESTDIR}/usr/sbin
+BLURCD_SHARE_DIR = ${DESTDIR}/usr/share/blurc
 
 
 all: blurcd #testBlurcd
@@ -61,8 +61,8 @@
 		else echo "Creating share directory: " $(BLURCD_SHARE_DIR);\
 		mkdir $(BLURCD_SHARE_DIR);\
 	fi
-	cp -i --reply=no ./etc/conf.d-blurcd /etc/conf.d/blurcd
-	cp -i --reply=no ./etc/init.d-blurcd /etc/init.d/blurcd
+	cp -i --reply=no ./etc/conf.d-blurcd ${DESTDIR}/etc/conf.d/blurcd
+	cp -i --reply=no ./etc/init.d-blurcd ${DESTDIR}/etc/init.d/blurcd
 	cp -i --reply=no ./etc/blurcd.conf ./etc/blurc.menu \
 	./etc/blurc.devices $(BLURCD_CONFIG_DIR)
 	cp -i --reply=no ./contrib/blurcc.jar ./contrib/blurcc.jad \
```

---

