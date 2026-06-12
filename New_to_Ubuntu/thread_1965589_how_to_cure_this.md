---
title: "how to cure this?"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by djhbrown on 2012-04-26
d@d-ThinkPad-T43:~$ javaws [http://files.gokgs.com/javaBin/cgoban.jnlp](http://files.gokgs.com/javaBin/cgoban.jnlp)

(java:2905): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(java:2905): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(java:2905): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(java:2905): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Exception in thread "Thread-1" java.lang.InternalError: Corrupt LRU file entries
	at net.sourceforge.jnlp.cache.CacheLRUWrapper$1.compare(CacheLRUWrapper.java:184)
	at net.sourceforge.jnlp.cache.CacheLRUWrapper$1.compare(CacheLRUWrapper.java:172)
	at java.util.Arrays.mergeSort(Arrays.java:1283)
	at java.util.Arrays.mergeSort(Arrays.java:1294)
	at java.util.Arrays.mergeSort(Arrays.java:1295)
	at java.util.Arrays.mergeSort(Arrays.java:1295)
	at java.util.Arrays.sort(Arrays.java:1223)
	at java.util.Collections.sort(Collections.java:176)
	at net.sourceforge.jnlp.cache.CacheLRUWrapper.getLRUSortedEntries(CacheLRUWrapper.java:172)
	at net.sourceforge.jnlp.cache.CacheUtil.getCacheFileIfExist(CacheUtil.java:325)
	at net.sourceforge.jnlp.cache.CacheUtil.getCacheFile(CacheUtil.java:306)
	at net.sourceforge.jnlp.cache.CacheEntry.<init>(CacheEntry.java:56)
	at net.sourceforge.jnlp.cache.ResourceTracker.initializeResource(ResourceTracker.java:769)
	at net.sourceforge.jnlp.cache.ResourceTracker.processResource(ResourceTracker.java:611)
	at net.sourceforge.jnlp.cache.ResourceTracker.access$500(ResourceTracker.java:72)
	at net.sourceforge.jnlp.cache.ResourceTracker$Downloader$1.run(ResourceTracker.java:1115)
	at net.sourceforge.jnlp.cache.ResourceTracker$Downloader$1.run(ResourceTracker.java:1113)
	at java.security.AccessController.doPrivileged(Native Method)
	at net.sourceforge.jnlp.cache.ResourceTracker$Downloader.run(ResourceTracker.java:1113)
	at java.lang.Thread.run(Thread.java:679)

---

