---
title: "c output issue"
date: 2012-09-11
forum: Programming Talk
---

### Post by pellyhawk on 2012-09-11
Why I got a weird content by "printf("serial buf = %s\n", buf);"? Why output is not 010203?

```
char buf[4] = {0x01,0x02,0x03,0x04};
unsigned char alarm_string[10];

for(i=0;i<ret;i++)
{
printf("%2.2x",(unsigned char)buf[i]);
alarm_string[i]=buf[i];
}

buf[3] = '\0';
[COLOR="Red"]printf("serial buf = %s\n", buf);[/COLOR]
```

Thanks

---

### Post by pellyhawk on 2012-09-11
Why add "\0" at the end of array, I still cannot output by %s?

---

### Post by Lux Perpetua on 2012-09-12
'1' is not the same as (char)0x01 (a.k.a. '\x01'). Your red statement writes the three characters '\x01', '\x02', and '\x03' to its output, which are non-printing characters.

---

