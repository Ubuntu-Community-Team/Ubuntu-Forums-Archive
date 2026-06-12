---
title: "deleting a &quot;value&quot; from a multimap and not the &quot;key&quot;"
date: 2011-12-05
forum: Programming Talk
---

### Post by vasavi on 2011-12-05
My requirement is to delete a "value" from the multimap and not the "key".
a key can have multiple values.
My requirement is similar to deleting a node from the linked list.
multimap::erase() is not erasing the "value" matching a "key".
 
 
Below is my code snippet.
void Clientqueues::clearSubscription(string name,string sessionid)
{
pair<multimap<string,string>::iterator,multimap<string,string>::iterator> i;
multimap<string, string>::iterator j;
i = registeredClientInfo.equal_range(name);
if (j == registeredClientInfo.end())
return;
for(j=i.first;j != i.second;++j)
{
if((j->second) == sessionid) registeredClientInfo.erase(j->second);
}
for(j=i.first;j != i.second;++j)
{
cout<<""<<j->second<<endl; **//This prints the erased values too;**
}
}
 
If this is not the right approach, could you plz suggest me a solution to delete a value from a multimap.
 
Thanks in advance.

---

### Post by GeneralZod on 2011-12-05
> **vasavi said:**
> 
multimap::erase() is not erasing the "value" matching a "key".


I *think* you want:

```

if((j->second) == sessionid) registeredClientInfo.erase(j);

```

Edit:

In fact, for properly conformant behaviour (since erase(j) invalidates j), you probably want:

```

 for(j=i.first;j != i.second;)
 {
     
    if((j->second) == sessionid) 
    {
        // Increments j while it is still valid; erases (and invalidates) "old" j.
        registeredClientInfo.erase(j++);
    }
    else
    {
        ++j;
    }
 }

```

(see e.g. [here](http://stackoverflow.com/questions/263945/what-happens-if-you-call-erase-on-a-map-element-while-iterating-from-begin-to).)

---

