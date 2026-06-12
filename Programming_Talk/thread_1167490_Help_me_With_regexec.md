---
title: "Help me With regexec"
date: 2009-05-22
forum: Programming Talk
---

### Post by huangyingw on 2009-05-22
Hello, my code is as bellow. I think my string "fafas.svn" should match my pattern ".(svn|cvs)$". While, subs[i].rm_so keep firmly giving me an incorrect answer of "0"...Rather confusing, could you give me a hand at this?
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h> 
#include <sys/types.h> 
#include <regex.h> 
  
#define SUBSLEN 10   
#define EBUFLEN 128   /*   error   buffer   length   */   
#define BUFLEN 102400   /*   matched   buffer   length   */   

int main(int argc, char** argv) 
{
	FILE *fp;
  size_t len;/*   store   error   message   length   */   
  regex_t re;/*   store   compilned   regular   expression   */   
  regmatch_t subs[SUBSLEN];/*   store   matched   string   position   */   
  char matched[BUFLEN];/*   store   matched   strings   */   
  char errbuf[EBUFLEN];/*   store   error   message   */   
  int err, i;
  size_t nmatch=0;
    
  memset( matched, 0x00,sizeof( matched));
  memset( errbuf, 0x00,sizeof( errbuf));

  char string[]="fafas.svn";   
  char pattern[]=".(svn|cvs)$";
  //char pattern[]="*afa*";
    
  printf("String:%s\n",string);   
  printf("Pattern:\"%s\"\n",pattern);   
    
  err=regcomp(&re,pattern,REG_EXTENDED);
  printf("%d\n",err);   
  
  if(err==REG_NOMATCH)   
  {   
  	fprintf(stderr,   "Sorry,   no   match   ...\n");   
  	regfree(&re);   
  	exit(0);   
  }
  else if(err)   
  {   
  	len=regerror(err,&re,errbuf,sizeof(errbuf));   
  	fprintf(stderr,   "error:   regexec:   %s\n",   errbuf);   
  	exit(1);   
  }
    
	err = regexec(&re, string, nmatch, subs,REG_EXTENDED);
	if(REG_NOMATCH==err)
	{
		 printf("no match\n");
	}
	else
	{
		printf("%d matched\n",(int)re.re_nsub);
		for(i=0;i<=re.re_nsub;i++)   
  	{   
  		if(i==0)   
  		{   
  			//printf("begin: %d, end: %d.\n",subs->rm_so,subs->rm_eo);
  			printf("begin: %d, end: %d.\n",subs[i].rm_so,subs[i].rm_eo);
  		}   
  		else   
  		{   
  			//printf("subexpression %d begin: %d, end: %d.\n",i,subs->rm_so,subs->rm_eo);
  			printf("subexpression %d begin: %d, end: %d.\n",i,subs[i].rm_so,subs[i].rm_eo);
  		}
  		len=subs[i].rm_eo-subs[i].rm_so;
  		memcpy(matched,string+subs[i].rm_so,len);
  		matched[len]='\0';
  		printf("match:%s\n",matched);
  	}
  	
	}
  regfree(&re);
  exit(0);
}

```

---

### Post by crdlb on 2009-05-23
I have never used the posix regex api, but from looking at man 3 regex, it looks like the problem is that you're passing 0 for nmatch, which is supposed to be the size of the pmatch array.

Secondly, 100KB is far too much to be allocating on the stack imho. It should work on a modern machine, but it's not a very good idea. Also, I don't see why string and pattern are arrays instead of simple char*'s.

Personally, I'd prefer to use something more powerful like PCRE (or GRegex if I were already using GLib, which uses a bundled PCRE).

---

### Post by huangyingw on 2009-05-23
> **crdlb said:**
> I have never used the posix regex api, but from looking at man 3 regex, it looks like the problem is that you're passing 0 for nmatch, which is supposed to be the size of the pmatch array.

Secondly, 100KB is far too much to be allocating on the stack imho. It should work on a modern machine, but it's not a very good idea. Also, I don't see why string and pattern are arrays instead of simple char*'s.

Personally, I'd prefer to use something more powerful like PCRE (or GRegex if I were already using GLib, which uses a bundled PCRE).
Great, thank you. 
BTW, I am interested in what you say 
> **crdlb said:**
> 
man 3 regex

My output of this command is:
```

No manual entry for regex in section 3

```
What is the problem? I think I am in an urgent need of such a man guide when programming with linux c.

---

### Post by crdlb on 2009-05-23
Install the manpages-dev package

---

### Post by huangyingw on 2009-05-23
> **crdlb said:**
> Install the manpages-dev package
Thanks.

---

### Post by rich1939 on 2009-05-23
> **huangyingw said:**
> Hello, my code is as bellow. I think my string "fafas.svn" should match my pattern ".(svn|cvs)$".

This isn't specific to your problem, but I use the following in my C programs to handle regular expression matches:

```

    zcPat = g_regex_new("^[0-9]{5}$|^[0-9]{5}-[0-9]{4}$", 0, 0, NULL);

```

That above code creates a pattern and then the code in my program to use it to validate the zipcode in a particular field in a form entry is as follows:

```

gboolean vzc(gchar *value, gboolean optional) // validate zipcode
{
    if (!g_regex_match(zcPat, value, 0, NULL) && !optional)
    {
        return FALSE;
    }
    return TRUE;
}

```

In some cases, the zipcode is optional, so I pass it TRUE to avoid the match.

After you're finished using the regular expression, you need to unref it, as follows:

```

    g_regex_unref(zcPat);

```

This approach seems a lot simpler to me.

---

### Post by huangyingw on 2009-05-24
> **rich1939 said:**
> This isn't specific to your problem, but I use the following in my C programs to handle regular expression matches:

```

    zcPat = g_regex_new("^[0-9]{5}$|^[0-9]{5}-[0-9]{4}$", 0, 0, NULL);

```

That above code creates a pattern and then the code in my program to use it to validate the zipcode in a particular field in a form entry is as follows:

```

gboolean vzc(gchar *value, gboolean optional) // validate zipcode
{
    if (!g_regex_match(zcPat, value, 0, NULL) && !optional)
    {
        return FALSE;
    }
    return TRUE;
}

```

In some cases, the zipcode is optional, so I pass it TRUE to avoid the match.

After you're finished using the regular expression, you need to unref it, as follows:

```

    g_regex_unref(zcPat);

```

This approach seems a lot simpler to me.
Yes, thanks, I will also try the method you mention.

---

