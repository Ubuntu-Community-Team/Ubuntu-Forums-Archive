---
title: "Strange Error message"
date: 2005-12-02
forum: Programming Talk
---

### Post by rock freak on 2005-12-02
Hey there guys just debugged my program i made and it has come up with a strange error message that i cant make any sense of!!!



It is as follows:

55: syntax error at end of input



and 55 is the last line  this is the lines of the script



```

write(fname,lname, &d, &m, &y);	/*write to file*/
	
	return(0);
}

```

any ideas guys???

Ollie

---

### Post by amohanty on 2005-12-02
> write(fname,lname, &d, &m, &y);	/*write to file*/
	
	return(0);
}

THis should be:
```

write(fname, lname, &d, &m, &y) [COLOR="Red"]**{**[/COLOR]
  return (0);
}

```

HTH
AM

---

