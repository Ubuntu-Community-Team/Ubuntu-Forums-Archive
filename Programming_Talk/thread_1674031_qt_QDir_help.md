---
title: "qt QDir help"
date: 2011-01-23
forum: Programming Talk
---

### Post by Woody1987 on 2011-01-23
I am getting an error when try to run this code:

```

void loadConfigFile()
{
    if(QFile::exists(QDir::homePath() + "/.test") == false)
    {
        QDir::cd(QDir::homePath());
        QDir::mkdir(".test");
    }
}

```

The error is:
> 
error: cannot call member function &#8216;bool QDir::cd(const QString&)&#8217; without object
error: cannot call member function &#8216;bool QDir::mkdir(const QString&) const&#8217; without object


---

### Post by Woody1987 on 2011-01-23
Solved.

```

QDir dir(QDir::homePath());
dir.mkdir(".test");
```

---

