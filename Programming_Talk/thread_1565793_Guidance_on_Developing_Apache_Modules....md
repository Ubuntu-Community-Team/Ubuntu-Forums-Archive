---
title: "Guidance on Developing Apache Modules..."
date: 2010-09-01
forum: Programming Talk
---

### Post by tyblogger5 on 2010-09-01
OK, I just downloaded Ubuntu 10.04 Server Edition and set up a LAMP server.  I'm trying to work on a project that involves development of an Apache module and I hit a roadblock.

***What I have done so far:***

I used the Installation CD to set up a LAMP server and a SSH server.  After restarting, I installed the build-essentials package and the apache2-threaded-dev package.  I navigate to /usr/include and I can see all the headers in the apache2 and apr-1.0 directories.  However, I can't figure out how I'm supposed to build the code.  This is the code that I wrote:

```

#include <apache2/httpd.h>
#include <apache2/http_protocol.h>
#include <apache2/http_config.h>

static int helloworld_handler(request_rec* r)
{
	if (!r->handler || strcmp(r->handler, "helloworld"))
		return DECLINED;

	if (r->method_number != M_GET)
		return HTTP_METHOD_NOT_ALLOWED;

	ap_set_content_type(r, "text/html;charset=ascii");
	ap_rputs("<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN">n", r);
	ap_rputs("<html><head><title>Hello World!</title></head>;", r);
	ap_rputs("<body><h1>Hello World!</h1></body></html>", r);
	return OK;
}

static void register_hooks(apr_pool_t* pool)
{
	ap_hook_handler(helloworld_handler, NULL, NULL, APR_HOOK_MIDDLE);
}

module AP_MODULE_DECLARE_DATA helloworld_module = {
	STANDARD20_MODULE_STUFF,
	NULL,
	NULL,
	NULL,
	NULL,
	NULL,
	register_hooks
};

```

When I try to build it using,

```
gcc -c test.c -o test.o
```

I get hundreds of errors, can anybody tell me what I am doing wrong and maybe give me some guidance as to how I am supposed to develop Apache modules?

Thanks,
Tariq

---

