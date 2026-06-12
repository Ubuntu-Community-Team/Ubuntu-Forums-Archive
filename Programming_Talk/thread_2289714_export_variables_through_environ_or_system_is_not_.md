---
title: "export variables through environ or system is not being updated"
date: 2015-08-06
forum: Programming Talk
---

### Post by subhav on 2015-08-06
Hi,

Actually i want to export some variables like the foll in python, but $PATH is not updated. Any help would be highly appreciated
 
export TOOLS="/volume/build"
export PATH=$TOOLS:$PATH

 os.system('export TOOLS="/volume/build"')
        os.system('export PATH=$TOOLS:$PATH')
        os.system( "echo $TOOLS")
        os.system("echo $PATH")

Thanks
subha

---

### Post by spjackson on 2015-08-06
Each call to os.system invokes a different shell and the export only applies to that shell. You can do this if it helps.
```

os.system('export TOOLS="/volume/build"; export PATH=$TOOLS:$PATH; echo $TOOLS; echo $PATH')

```

---

