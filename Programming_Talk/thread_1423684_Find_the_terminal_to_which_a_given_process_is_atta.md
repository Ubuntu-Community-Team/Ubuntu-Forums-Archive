---
title: "Find the terminal to which a given process is attached to"
date: 2010-03-06
forum: Programming Talk
---

### Post by DBQ on 2010-03-06
Hi everybody.

I know I can find out to which terminal a given process is attached to by using ps. 

Is there a way to do this programatically? Ie in C. 

Also is there a way to find all processes which are attached to some terminal?

---

### Post by Barriehie on 2010-03-07
Like:
```

ps aux | grep **process_name**
```

or, the other way around:
```

ps aux | grep tty**some_number**
```

---

