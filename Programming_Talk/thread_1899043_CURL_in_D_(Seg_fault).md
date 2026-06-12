---
title: "CURL in D (Seg fault)"
date: 2011-12-22
forum: Programming Talk
---

### Post by Petrolea on 2011-12-22
Hi everyone!

I just started using the curl library and have no idea why this code is seg faulting. It is in D programming language. 

[PHP]
#!/usr/bin/rdmd -w
import std.stdio;
import etc.c.curl;

int main()
{
	curl_global_init(CurlGlobal.all);
	auto easy_handle = curl_easy_init();
	
	curl_easy_setopt(easy_handle, CurlOption.url, "http://24ur.com"); //SEG FAULT
	
	curl_easy_cleanup(easy_handle);
	curl_global_cleanup();
	return 0;
}
[/PHP]

It segfaults in line with curl_easy_setopt(...). Anyone knows why that might be happening?

Thanks in advance!

---

### Post by deadalnix on 2012-01-04
Hi,

Can you tell us what compiler are you using and which version ?

As far as I know gdc in ubuntu's repository is broken. I don't jnow if it has been fixed in recent version of ubuntu.

You can use dmd, the last version is 2.057 . You can also compile gdc by yourself as mentionned here : [https://bitbucket.org/goshawk/gdc/wiki/Home](https://bitbucket.org/goshawk/gdc/wiki/Home) (but you'll have D version 2.055, the main changement is about inout : [http://drdobbs.com/blogs/cpp/231902461](http://drdobbs.com/blogs/cpp/231902461) ).

I can't help you that much without more details.

---

### Post by Petrolea on 2012-01-04
> **deadalnix said:**
> Hi,

Can you tell us what compiler are you using and which version ?

As far as I know gdc in ubuntu's repository is broken. I don't jnow if it has been fixed in recent version of ubuntu.

You can use dmd, the last version is 2.057 . You can also compile gdc by yourself as mentionned here : [https://bitbucket.org/goshawk/gdc/wiki/Home](https://bitbucket.org/goshawk/gdc/wiki/Home) (but you'll have D version 2.055, the main changement is about inout : [http://drdobbs.com/blogs/cpp/231902461](http://drdobbs.com/blogs/cpp/231902461) ).

I can't help you that much without more details.

I use dmd. But that's old problem and I used curl for D this time. Will mark it as solved, but thanks for help anyway!

---

