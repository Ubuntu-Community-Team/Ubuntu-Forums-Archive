---
title: "Weird syntax error in ubuntu terminal"
date: 2008-09-08
forum: Programming Talk
---

### Post by niccholaspage on 2008-09-08
So heres just some fun code I messed with:
```

if nga=1 {
zenity  --info --title "NGA" --text "Computer Validated.This computer uses NGA."
}
else
{
zenity  --info --title "NGA" --text "Computer Validated.This computer does not use NGA."
}
fi

```I get this error while executing the code:
> validate-nga.sh: 3: Syntax error: "}" unexpected (expecting "then")Oh and is nga=1 right to read an environment variable from the system?

---

### Post by mssever on 2008-09-08
> **niccholaspage said:**
> So heres just some fun code I messed with:
```

if [[ $nga -eq 1 ]]; then
  zenity  --info --title "NGA" --text "Computer Validated.This computer uses NGA."
else
  zenity  --info --title "NGA" --text "Computer Validated.This computer does not use NGA."
fi
```

---

### Post by niccholaspage on 2008-09-08
OH! The programming language I used before let me use { and } without any problems.Thank you.

---

### Post by DaymItzJack on 2008-09-08
> **niccholaspage said:**
> OH! The programming language I used before let me use { and } without any problems.Thank you.

Every programming language is different.

---

### Post by niccholaspage on 2008-09-08
Oh and one more thing....The environment variable should be set like this,Right?
```
export nga=1
```
I used the script and it said my computer is not validated.

---

### Post by mssever on 2008-09-08
> **niccholaspage said:**
> Oh and one more thing....The environment variable should be set like this,Right?
```
export nga=1
```I used the script and it said my computer is not validated.
Yes, but if you export a variable, that only applies to processes started by that shell. So if you export from a terminal window, then click a button to launch your script via a GUI, it won't work.

---

### Post by niccholaspage on 2008-09-08
Than how do I set it so it will use that variable anytime?

---

### Post by CptPicard on 2008-09-09
I'm going to get flamed for this, but you should really try a proper programming language such as Python... ;)

---

### Post by mssever on 2008-09-09
> **niccholaspage said:**
> Than how do I set it so it will use that variable anytime?
Well, if you want the variable to apply to all users, you can set it in /etc/profile. You can also probably hack one of the GDM scripts to set it. But the easiest thing would probably be to write the value to a file and read that instead of messing with an environment variable.
> **CptPicard said:**
> I'm going to get flamed for this, but you should really try a proper programming language such as Python... ;)
Actually, I don't think that switching to Python will solve an environment variable problem. I don't know what the OP is trying to accomplish, but there may be other reasons why switching languages might be a good idea. It's also possible that bash could be an acceptable language for this task--although the OP should really read up on bash programming if he/she is going to keep bash. [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

### Post by CptPicard on 2008-09-09
> **mssever said:**
> 
Actually, I don't think that switching to Python will solve an environment variable problem. ...  It's also possible that bash could be an acceptable language for this task

Yes, true. I just get the feel that there is a large probability that bash is not being a fully informed choice here :)

---

### Post by mssever on 2008-09-09
> **CptPicard said:**
> Yes, true. I just get the feel that there is a large probability that bash is not being a fully informed choice here :)
I agree. As for the OP's original issue with curly braces, Python also has that "problem": 
```
[COLOR=#000080]**>>> **[/COLOR][COLOR=#008000]**from**[/COLOR] [COLOR=#0000ff]**__future__**[/COLOR] [COLOR=#008000]**import**[/COLOR] braces
[COLOR=#808080]  File "<stdin>", line 1
SyntaxError: ***not a chance***
[/COLOR][COLOR=#000080]**>>> **[/COLOR]

```:)

---

