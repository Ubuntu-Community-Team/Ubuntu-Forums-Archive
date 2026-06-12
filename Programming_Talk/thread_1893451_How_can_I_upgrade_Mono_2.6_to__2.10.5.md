---
title: "How can I upgrade Mono 2.6 to  2.10.5  ?"
date: 2011-12-10
forum: Programming Talk
---

### Post by hoboy on 2011-12-10
I am using Mono 2.6 on Ubuntu Oneiric (11.10).
How can I upgrade mono to mono 2.10 ?

---

### Post by MadCow108 on 2011-12-10
ubuntu 11.10 has mono 2.10 by default.
```

$ mono --version
Mono JIT compiler version 2.10.5 (Debian 2.10.5-1)
Copyright (C) 2002-2011 Novell, Inc, Xamarin, Inc and Contributors. www.mono-project.com
	TLS:           __thread
	SIGSEGV:       altstack
	Notifications: epoll
	Architecture:  amd64
	Disabled:      none
	Misc:          softdebug 
	LLVM:          supported, not enabled.
	GC:            Included Boehm (with typed GC and Parallel Mark)
$ lsb_release -a
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric
```

---

