---
title: "Using C programming language to access internet (2)"
date: 2007-10-05
forum: Programming Talk
---

### Post by NuNn DaDdY on 2007-10-05
I'm currently beginning a project in which the task is to create a terminal based rss reader using C.  I was wondering where I would find documentation on how to use C to have online access. Thanks.

---

### Post by LaRoza on 2007-10-05
Socket programming, [http://www.uwo.ca/its/doc/courses/notes/socket/](http://www.uwo.ca/its/doc/courses/notes/socket/)

For Python, it would be much easier using httplib [http://docs.python.org/lib/module-httplib.html]("http://docs.python.org/lib/module-httplib.html")

---

### Post by Wybiral on 2007-10-05
[http://curl.haxx.se/libcurl/](http://curl.haxx.se/libcurl/)

---

### Post by slavik on 2007-10-06
some code to get your started. this goes and fetches the main page from google and prints it to terminal (along with the response header)

```

/*
 *      wget_sortof.c
 *
 *      Copyright 2007 Vyacheslav Goltser <slavikg@gmail.com>
 *
 *      This program is free software; you can redistribute it and/or modify
 *      it under the terms of the GNU General Public License as published by
 *      the Free Software Foundation; either version 3 of the License, or
 *      (at your option) any later version.
 *
 *      This program is distributed in the hope that it will be useful,
 *      but WITHOUT ANY WARRANTY; without even the implied warranty of
 *      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 *      GNU General Public License for more details.
 *
 *      You should have received a copy of the GNU General Public License
 *      along with this program; if not, write to the Free Software
 *      Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301, USA.
 */

/* get the main page from google.com */

#include <stdio.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <netdb.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>

int main(int argc, char** argv)
{
	struct sockaddr_in servaddr;
	struct hostent *hp;
	int sock_id;
	char message[1024*1024];
	char msglen;
	char request[] = "GET /index.html HTTP/1.0\n"
	"From: slava!!!\nUser-Agent: wget_sortof by slava\n\n";
	
	//Get a socket	
	if((sock_id = socket(AF_INET, SOCK_STREAM, 0)) == -1) {
		fprintf(stderr,"Couldn't get a socket.\n"); exit(EXIT_FAILURE);
	}
	else {
		fprintf(stderr,"Got a socket.\n");
	}
	
	//book uses bzero which my man pages say is deprecated
	//the man page said to use memset instead. :-)
	memset(&servaddr,0,sizeof(servaddr));
	
	//get address for google.com
	if((hp = gethostbyname("google.com")) == NULL) {
		fprintf(stderr,"Couldn't get an address.\n"); exit(EXIT_FAILURE);
	}
	else {
		fprintf(stderr,"Got an address.\n");
	}
	
	//bcopy is deprecated also, using memcpy instead
	memcpy((char *)&servaddr.sin_addr.s_addr, (char *)hp->h_addr, hp->h_length);
	
	//fill int port number and type
	servaddr.sin_port = htons(80);
	servaddr.sin_family = AF_INET;
	
	//make the connection
	if(connect(sock_id, (struct sockaddr *)&servaddr, sizeof(servaddr)) != 0) {
		fprintf(stderr, "Couldn't connect.\n");
	}
	else {
		fprintf(stderr,"Got a connection!!!\n");
	}
	
	//NOW THE HTTP PART!!!
	
	//send the request
	write(sock_id,request,strlen(request));
	
	//read the response
	msglen = read(sock_id,message,1024*1024);
	
	//print the reasponse
	fprintf(stdout,"%s",message);
	
	return 0;
}
```

---

### Post by Wybiral on 2007-10-06
Reading the feed is pretty trivial, especially if you use a good library (such as libCurl).

```

// gcc source.c -lcurl

#include <stdlib.h>
#include <curl/curl.h>

void download_feed(FILE *dst, const char *src)
{
    CURL *handle = curl_easy_init();
    curl_easy_setopt(handle, CURLOPT_URL, src);
    curl_easy_setopt(handle, CURLOPT_WRITEDATA, dst);
    curl_easy_perform(handle);
}

int main()
{
    FILE *feed = fopen("feed.xml", "rw");
    download_feed(feed, "http://feeds.feedburner.com/ICanHasCheezburger");
    fclose(feed);
    return 0;
}

```

Parsing it will be the fun part. Does this have to be a generic feed reader that can reed any rss/atom feeds? Or just for one specific feed that you can tailor to it's format?

String handling and parsing are a pain in C, if it's possible to avoid C, using a higher level language would help.

Here's an example of a simple feed reader in Python (using the feedparser module which you can grab from synaptic) that writes the contents to an HTML file. You could easily modify this to write the contents to the terminal.

```

import feedparser

def title(feed):
    if entry.has_key("title"):
        return entry["title"]
    else:
        return "[Untitled]"

def content(feed):
    if entry.has_key("content"):
        out = ""
        for content in entry.content:
            out += content.value
        return out
    elif entry.has_key("desciption"):
        return entry.description
    return "[Empty]"

feed = feedparser.parse("http://feeds.feedburner.com/ICanHasCheezburger")
out = "<html><body><center>"
for entry in feed['entries']:
    out += "<b>%s</b><br/>%s<hr/><br/>" % (title(feed), content(feed))
out += "</center></body></html>"
open("feed.html", "w").write(out.encode('ascii', 'ignore'))

```

---

### Post by Sef on 2007-10-09
Locking this thread since it has gotten off-topic.   If you want to help the OP with a reply to their question, click [right here]("http://ubuntuforums.org/showthread.php?t=571362").

---

