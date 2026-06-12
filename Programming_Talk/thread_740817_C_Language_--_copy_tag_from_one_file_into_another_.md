---
title: "C Language -- copy tag from one file into another file"
date: 2008-03-31
forum: Programming Talk
---

### Post by Zedrick on 2008-03-31
I am using Atheme IRC Services,  and I am wanting to make the channel memos a little bit neater.



When you send a memo to the channel,  it displays it like this,


-MemoServ- Memo 1 - Sent by Zedrick, Mar 31 20:02:26 2008
-MemoServ- ------------------------------------------
-MemoServ- [#channel] memo message



I am wanting to change the position of the #channel name to be up the top next to the date and time - to say for #channel -- and to add in the word for.


-MemoServ- Memo 1 - Sent by Zedrick, Mar 31 20:02:26 2008 for #channel
-MemoServ- ------------------------------------------
-MemoServ- memo message



The send of the memo copies the channel name and the memo message to the read.c file



This is the line for the channel name and memo message,

sendops.c

mc->name -- is the name of the channel,  and m is the memo message

```
		/* Malloc and populate struct */
		memo = smalloc(sizeof(mymemo_t));
		memo->sent = CURRTIME;
		memo->status = MEMO_CHANNEL;
		strlcpy(memo->sender,si->smu->name,NICKLEN);
		snprintf(memo->text, MEMOLEN, "[\2%s\2] %s", mc->name, m);
```



This is the line where it reads the memo,

read.c

```
			command_success_nodata(si, 
				"\2Memo %d - Sent by %s, %s\2",i,memo->sender, strfbuf);
			
			command_success_nodata(si, 
				"------------------------------------------");
			
			command_success_nodata(si, "%s", memo->text);
			
			if (!readnew)
				return;
			if (++numread >= MAX_READ_AT_ONCE && si->smu->memoct_new > 0)
			{
				command_success_nodata(si, _("Stopping command after %d memos."), numread);
				return;
			}
		}
		i++;
	}
```



how do I change the position of the #channel name to be next to the date and time to say - for #channel -- and to add in the word for ?

I have attached both the sendops and read file -- zip attachment

---

### Post by Zugzwang on 2008-03-31
Ok, so here's my try. It may or may not work because:
[LIST]
[*] Your problem is quite specific and I don't have a clue how the rest of the program looks. Especially I'm only guessing what command_success_nodata does
[*] Also the buffer allocated by command_success_nodata might be too small to hold the new message.
[/LIST]

You need to extend the structure mymemo_t by a channel field (say, of length MEMOLEN). Then you might be able to use:

First snipplet:
[PHP]
/* Malloc and populate struct */
memo = smalloc(sizeof(mymemo_t));
memo->sent = CURRTIME;
memo->status = MEMO_CHANNEL;
strlcpy(memo->sender,si->smu->name,NICKLEN);
snprintf(memo->text, MEMOLEN, "%s", m);
snprintf(memo->channel, MEMOLEN, "%s", mc->name );
[/PHP]

Second snipplet:
[PHP]
command_success_nodata(si,  "\2Memo %d - Sent by %s, %s\2 for %s",i,memo->sender, memo->channel, strfbuf);
command_success_nodata(si, "------------------------------------------");
command_success_nodata(si, "%s", memo->text);
[/PHP]

Hope that helps.

---

### Post by Zedrick on 2008-04-01
It is coming up with error: structure has no member named channel -- when you ./setup to add the changes in.

It needs a structure member name for channel.

I tried adding in a structure mychan_t *channel; -- which didn't work.

```
snprintf(memo->channel, MEMOLEN, "%s", mc->name);
```



This is the structure line,

sendops.c

```

	/* misc structs etc */
	myuser_t *tmu;
	node_t *n, *tn;
	mymemo_t *memo;
	mychan_t *mc;
	int sent = 0, tried = 0;
	boolean_t ignored;
```




I am gussing the word "for" needs its own %s to be included in the memo->channel line, to have it say for #channel name - that gets attached to the read.c line

```
snprintf(memo->channel, MEMOLEN, "%s %s", for, mc->name);
```

```
command_success_nodata(si,  "\2Memo %d - Sent by %s, %s\2 for %s",i,memo->sender, memo->channel, strfbuf);
```




The zip attachment has the whole file for both sendops.c and read.c -- in the first post.

---

### Post by ruy_lopez on 2008-04-01
> **Zedrick said:**
> It is coming up with error: structure has no member named channel


> **Zugzwang said:**
> 
You need to extend the structure mymemo_t by a channel field (say, of length MEMOLEN).

The mymemo_t struct isn't defined in read.c or sendops.c. That means it's probably defined in "atheme.h".

---

### Post by Zedrick on 2008-04-01
Thanks ruy_lopez

I haven't been able to find the structure spot we need to do this.

We should be right when we find it.

The install file for Atheme is at [http://www.atheme.net/]("http://www.atheme.net/")

sendops.c and read.c are in modules/memoserv


This is atheme.h,

in the folder include

```
/*
 * Copyright (c) 2003-2004 E. Will et al.
 * Rights to this code are documented in doc/LICENSE.
 *
 * Includes most headers usually needed.
 *
 * $Id: atheme.h 8375 2007-06-03 20:03:26Z pippijn $
 */

#ifndef ATHEME_H
#define ATHEME_H

/* *INDENT-OFF* */

#define E extern
#define DLE

#include "sysconf.h"
#include "stdinc.h"
#include "i18n.h"
#include "common.h"
#include "dlink.h"
#include "object.h"
#include "event.h"
#include "balloc.h"
#include "connection.h"
#include "hook.h"
#include "linker.h"
#include "atheme_string.h"
#include "atheme_memory.h"
#include "table.h"
#include "servers.h"
#include "channels.h"
#include "module.h"
#include "crypto.h"
#include "culture.h"
#include "base64.h"
#include "md5.h"
#include "sasl.h"
#include "match.h"
#include "sysconf.h"
#include "account.h"
#include "tools.h"
#include "confparse.h"
#include "global.h"
#include "flags.h"
#include "metadata.h"
#include "phandler.h"
#include "servtree.h"
#include "services.h"
#include "commandtree.h"
#include "users.h"
#include "sourceinfo.h"
#include "symbolmatrix.h"

#include "inline/account.h"
#include "inline/channels.h"
#include "inline/connection.h"

#endif /* ATHEME_H */

/* vim:cinoptions=>s,e0,n0,f0,{0,}0,^0,=s,ps,t0,c3,+s,(2s,us,)20,*30,gs,hs ts=8 sw=8 noexpandtab
 */

```

---

### Post by Zugzwang on 2008-04-01
Dear OP, use fgrep to find the header file in which the structure is located.

```

fgrep -H "mymemo_t" *.h 

```

---

### Post by Zedrick on 2008-04-01
I did manage to find the spot soon after I posted -- in account.h

sorry for that

```
#ifndef ACCOUNT_H
#define ACCOUNT_H

typedef struct myuser_name_ myuser_name_t;
typedef struct chanacs_ chanacs_t;
typedef struct kline_ kline_t;
typedef struct mymemo_ mymemo_t;
typedef struct svsignore_ svsignore_t;
```


```
/* struct for account memos */
struct mymemo_ {
	char	 sender[NICKLEN];
	char 	 text[MEMOLEN];
        char 	 channel[MEMOLEN];
	time_t	 sent;
	unsigned int status;
	list_t	 metadata;
};
```


adding in char channel[MEMOLEN]; worked and put the #channel name up the top.

just need to play with it to get it working right,  got it with just #channel without the for #channel.

---

### Post by Zedrick on 2008-04-01
I have done it

-MemoServ- Memo 1 - Sent by Zedrick, for #channel, Apr 02 10:40:40 2008
 -MemoServ- ------------------------------------------
 -MemoServ- memo message


Thank You so kindly



account.h

```
/* struct for account memos */
struct mymemo_ {
	char	 sender[NICKLEN];
	char 	 channel[CHANNELLEN];
        char 	 text[MEMOLEN];
	time_t	 sent;
	unsigned int status;
	list_t	 metadata;
};
```



sendops.c

```
		/* Malloc and populate struct */
		memo = smalloc(sizeof(mymemo_t));
		memo->sent = CURRTIME;
		memo->status = MEMO_CHANNEL;
		strlcpy(memo->sender,si->smu->name,NICKLEN);
                snprintf(memo->channel, CHANNELLEN, "for %s,", mc->name);
		snprintf(memo->text, MEMOLEN, "%s", m);
```



read.c

```
			command_success_nodata(si, 
				"\2Memo %d - Sent by %s, %s %s\2",i,memo->sender, memo->channel, strfbuf);
			
			command_success_nodata(si, 
				"------------------------------------------");
			
			command_success_nodata(si, "%s", memo->text);
```

---

### Post by Zedrick on 2008-04-15
This has only half worked for the channel memo to look like this,


-MemoServ- Memo 1 - Sent by Zedrick, for #channel, Apr 02 10:40:40 2008
-MemoServ- ------------------------------------------
-MemoServ- memo message


When you shutdown,  the channel name disappears from up the top there and I tried changing the channel name on channellen to be memolen which the channel name still disappears.


When the channel name and memo message are on the same line in the code,  the name of the channel stays there and does not disappear.


does anyone know why the channel name disappears on shutdown when you read the memo?

---

