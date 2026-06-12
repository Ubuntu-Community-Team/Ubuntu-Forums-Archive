---
title: "Is this safe ?"
date: 2010-05-04
forum: Programming Talk
---

### Post by dragos2 on 2010-05-04
Is this a safe construction in a bash script if the files contains spaces in their name:
```

if cp -p -r $S/folder/path/$Folder $S/folder/path/${Number}_${projectName}; then
# some command
fi

```

---

### Post by wmcbrine on 2010-05-04
No. But put some quotes in, and it will be.

---

### Post by dragos2 on 2010-05-05
> **wmcbrine said:**
> No. But put some quotes in, and it will be.

Like this:
```

if cp -p -r "$S"/folder/path/"$Folder" "$S"/folder/path/"$Number"_"$projectName"; then
# some command
fi

```

I pulled out the {} around variables, I don't remeber why I needed them.

---

### Post by MadCow108 on 2010-05-05
you have to quote the whole thing not just the variables
inside double quotes bash expands variables, so you can leave them in

the braces are necessary when placing non-space characters behind variable names so the shell can distinguish them from text:
$VARsuffix = variable with name VARsuffix
${VAR}suffix = variable with name VAR and suffix appended

---

### Post by dragos2 on 2010-05-05
> **MadCow108 said:**
> you have to quote the whole thing not just the variables
inside double quotes bash expands variables, so you can leave them in

the braces are necessary when placing non-space characters behind variable names so the shell can distinguish them from text:
$VARsuffix = variable with name VARsuffix
${VAR}suffix = variable with name VAR and suffix appended

So this would be the correct version:

```

if cp -p -r "$S/folder/path/$Folder" "$S/folder/path/${Number}_${projectName}"; then
# some command
fi

```

---

### Post by MadCow108 on 2010-05-05
I'd say yes
just try it on a test folder or with an the command in a echo first:
echo "cp -p -r \"$blabla\" \"$blub\""
(\" escapes quotes so they are shown)

---

