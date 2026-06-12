---
title: "program crashes, memory allocation I think"
date: 2008-11-13
forum: Programming Talk
---

### Post by AussieGuy69 on 2008-11-13
Hi

Im trying to send a header to a socket, and I want to print the header so that I can see it for myself before its sent to make sure its fine.

The line that crashes the program is the "printf" line (5592). take out the printf line and send() complains its an invalid address. The rest seems to run fine.

How would I make it so that printf can print the string representation of the header (pointed to by *headers)? Should I even be using printf?

gchar* header_fmt_to_string  	(   	gpointer   	 o  	 )  is the declaration for header_fmt_to_string, by the way.

5572                                 gint fd;
5573                                 gchar *headers;
5574                                 int headers_size;
5575                                 struct header_fmt *fmt;
5576 
5577                                 fmt = (struct header_fmt *)malloc(250);
5578                                 headers = (gchar *)malloc(1000);
5579 
5580 
5581                                 //get the file descriptor
5582                                 fd = socket_evt_fd(n->socket);
5583                                 //format the header
5584                                 fmt = header_fmt_make("GET /get// HTTP/1.1", ", ", 100);
5585 
5586                                 //send the header string
5587 
5588                                 headers = *header_fmt_to_string(fmt);
5589                                 //headers = "\n\nabcdefg\n\n";
5590                                 headers_size = sizeof(headers);
5591                                 printf("\n%s\n",headers);

---

### Post by dwhitney67 on 2008-11-13
> **AussieGuy69 said:**
> Hi

Im trying to send a header to a socket, and I want to print the header so that I can see it for myself before its sent to make sure its fine.

The line that crashes the program is the "printf" line (5592). take out the printf line and send() complains its an invalid address. The rest seems to run fine.

How would I make it so that printf can print the string representation of the header (pointed to by *headers)? Should I even be using printf?

gchar* header_fmt_to_string  	(   	gpointer   	 o  	 )  is the declaration for header_fmt_to_string, by the way.

5572                                 gint fd;
5573                                 gchar *headers;
5574                                 int headers_size;
5575                                 struct header_fmt *fmt;
5576 
5577                                 fmt = (struct header_fmt *)malloc(250);
5578                                 headers = (gchar *)malloc(1000);
5579 
5580 
5581                                 //get the file descriptor
5582                                 fd = socket_evt_fd(n->socket);
5583                                 //format the header
5584                                 fmt = header_fmt_make("GET /get// HTTP/1.1", ", ", 100);
5585 
5586                                 //send the header string
5587 
5588                                 headers = *header_fmt_to_string(fmt);
5589                                 //headers = "\n\nabcdefg\n\n";
5590                                 headers_size = sizeof(headers);
5591                                 printf("\n%s\n",headers);
Why are you allocating memory for 'headers' if you plan moments later to use the variable to point to another address after calling header_fmt_to_string()?

The sizeof(headers) returns the value of 4; this is probably not what you intended for line 5590.  You probably are interested in the string length of 'headers'.

As for the printf() call, I believe it is fine.  I think what is biting you is line 5588, but it is hard to tell.  Try running your app through the gdb debugger.

P.S.  It sure would be nice if you upgraded gcc to use newer standards (e.g. gnu99 or std99), so that you could declare and initialize your variables at the same time.  It nauseating to see variables declared at the opening of a function, and then not used until later.

For example:
```

struct header_fmt* fmt = header_fmt_make("GET /get// HTTP/1.1", ", ", 100);
gchar* headers = header_fmt_to_string(fmt);
guint headers_size = strlen(headers);
...
printf("\n%s\n",headers);
...
gint fd = socket_evt_fd(n->socket);
...
header_fmt_free(fmt);
...

```

---

