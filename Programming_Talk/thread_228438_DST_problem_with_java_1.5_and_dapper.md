---
title: "DST problem with java 1.5 and dapper"
date: 2006-08-03
forum: Programming Talk
---

### Post by statuz on 2006-08-03
Hi all,
I've got 2 machine (updated daily) running dapper with java 1.5; I found that "strangeness":

Executing this simple code:

import java.util.*;

public class Test
{
   public static void main(String[] args)
   {
      GregorianCalendar gc = new GregorianCalendar();
      System.out.println("TIME: "+gc.get(Calendar.HOUR_OF_DAY)+":"+gc.get(Calendar.MINUTE));
      System.out.println("ZONE: "+gc.get(Calendar.ZONE_OFFSET)/(60*60*1000));
      System.out.println("DST: "+gc.get(Calendar.DST_OFFSET)/(60*60*1000));
   }
}

this is the output:

TIME: 9:5
ZONE: 1
DST: 0

but if I execute "date" from bash I've got (I'm in Italy):

gio ago  3 10:05:15 CEST 2006

What I want to say is that on ubuntu machines java doesn't recongnize DST and therefore every java date miss an hour; I executed the same code on windows, debian, suse and osx and the result is correct:

ZONE: 1
DST: 1

Someone can tell me something about this and if this happens only to me?
Thank you in advance

---

