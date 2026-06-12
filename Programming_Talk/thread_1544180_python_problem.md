---
title: "python problem"
date: 2010-07-20
forum: Programming Talk
---

### Post by mohit.joshi on 2010-07-20
typedef [COLOR=yellow][COLOR=blue]struct[/COLOR]
[/COLOR]{
 unsigned int   priority;
 unsigned int   prioritisedBitRate;
 unsigned int   bucketSizeDur;
 unsigned int  logchannelGrp;
}[COLOR=orange]logicalChannelExplicitCnf_st[/COLOR];
these type of files... i have to change it into the files mentioned below  using python in unix
 
class [COLOR=orange]logicalChannelExplicitCnf_st[/COLOR]([COLOR=blue]strucure)[/COLOR]  #structure comes from struct,if union i                                                                   #is their then in union it should be union
     _fields_=[("priority",c_int32),("prioritisedBitRate",c_int32),   ("bucketSizeDur",c_int32 ),("logchannelGrp",)c_int32]
 
 
#c_int32 is used instead of unsigned int, c_char for char

---

### Post by mohit.joshi on 2010-07-20
please help me or i am fired.. this is my second day and my boss has given this.. i have nevr worked on python

---

### Post by surfer on 2010-07-20
this should get you started: you could extract the types and stuff with the regex module. all you have to do now is print them in the appropriate way... and check for the cases that do not match the above example.

```

#!/usr/bin/python
# -*- coding: utf-8 -*-

import re

c_str = '''
typedef struct
{
unsigned int priority;
unsigned int prioritisedBitRate;
unsigned int bucketSizeDur;
unsigned int logchannelGrp;
}logicalChannelExplicitCnf_st;
'''


re_typedef = re.compile( '''
      (?P<typedef_struct>typedef\ struct)         # header
      (?P<whitespace0>[^{])                       # whitespace
      (?P<opening_bracket>{)
      (?P<statement>[^}]*)
      (?P<closing_bracket>})
      (?P<class>[^;]*)
      ;
       ''',
       re.MULTILINE | re.VERBOSE)

res_typedef = re_typedef.search(c_str)

print res_typedef.group('class')

stmt_strg = res_typedef.group('statement')
print stmt_strg


re_statement = re.compile( '''
      (?P<type>\w+)
      (?P<whitespace0>\ )
      (?P<type2>\w+)
      (?P<whitespace1>\ )
      (?P<var_name>\w+)
      ;
       ''',
       re.MULTILINE | re.VERBOSE)

res_statement = re_statement.finditer(stmt_strg)

# print res_statement.group('var_name')
for item in res_statement:
    print item.group('var_name')

```

---

### Post by mohit.joshi on 2010-07-21
thanks for the help..
but this doesnt work..

---

### Post by surfer on 2010-07-21
what exactly does not work?

it does not solve your whole problem of course, but it should get you started to get there. all it does for the moment is parse the above structure. what you have to do is rearrange the output as you need it.

---

### Post by mohit.joshi on 2010-07-21
actually m just a intern.. not a great programmer.. i dint get the code.. so editing it is a tedious job

---

### Post by mohit.joshi on 2010-08-02
typedef [COLOR=yellow][COLOR=blue]struct [/COLOR][COLOR=#ffa500]logicalChannelExplicitCnf_st[/COLOR]
[/COLOR]{
unsigned int priority;
unsigned int prioritisedBitRate;
unsigned int bucketSizeDur;
unsigned int logchannelGrp;
};
these type of files... i have to change it into the files mentioned below using python in unix

class [COLOR=orange]logicalChannelExplicitCnf_st[/COLOR]([COLOR=blue]strucure)[/COLOR] #structure comes from struct,if union i #is their then in union it should be union
_fields_=[("priority",c_int32),("prioritisedBitRate",c_int32 ), ("bucketSizeDur",c_int32 ),("logchannelGrp",)c_int32]


#c_int32 is used instead of unsigned int, c_char for char
[IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG] [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=9612059")   [IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG]

---

### Post by mohit.joshi on 2010-08-02
well the replacing of c_char can be done by replace command.. help me through the string comparison

---

### Post by mohit.joshi on 2010-08-04
i am new to the programming world .. and brand new to python...
typedef [COLOR=yellow][COLOR=blue]struct [/COLOR][COLOR=#ffa500]logicalChannelExplicitCnf_st[/COLOR]
[/COLOR]{
unsigned int [COLOR=purple]priority[/COLOR];
unsigned int prioritisedBitRate;
unsigned int bucketSizeDur;
unsigned int logchannelGrp;
};
i have to change it into the files mentioned below using **[COLOR=#ff0000]python[/COLOR]** in unix

class [COLOR=orange]logicalChannelExplicitCnf_st[/COLOR]([COLOR=blue]strucure)[/COLOR] #structure comes from struct,if union i #is their then in union it should be union
_fields_=[("[COLOR=purple]priority[/COLOR]",c_int32),("prioritisedBitRate",c_in t32 ), ("bucketSizeDur",c_int32 ),("logchannelGrp",)c_int32]


c_int 32 is for unsigned int..
how will i read the file and then store these variables in array and then access them to write in other file...
or is there any other method of doin it????

---

### Post by cariboo on 2010-08-04
Please don't create multiple threads on the same subject, I have merged your three threads.

---

