---
title: "[Python] if, if not, else, else keeps executing"
date: 2009-05-16
forum: Programming Talk
---

### Post by dodle on 2009-05-16
This is a section of my code.  The [color=red]else[/color] statement executes no matter what.  
[php]...
...
...
    def onBuild(self, event):
        nameVal = self.name_widg.GetValue()
        verVal = self.ver_widg.GetValue()
        archVal = self.arch_widg.GetValue()
        execVal = self.xpath_widg.GetValue()
        custVal = self.cust_widg.GetValue()
        optfilesVal = self.optfiles_widg.GetValue()
        destVal = self.dest_widg.GetValue()
        treeVal = ("%s/%s_tmp" % (destVal,nameVal))
        iconVal = self.icon_widg.GetValue()
        catVal = self.m_cat_widg.GetValue()
        m_nameVal = self.m_name_widg.GetValue()
        
        
        if nameVal == "":
            error_dia = wx.MessageDialog(self, "Under \"Info1\" tab\n\nSpecify a name for the project",
                                         "Software Name Error", wx.OK|wx.ICON_ERROR)
            error_dia.ShowModal()
            error_dia.Close()
        if verVal == "":
            error_dia = wx.MessageDialog(self, "Under \"Info1\" tab\n\nSpecify a version for the project",
                                         "Software Version Error", wx.OK|wx.ICON_ERROR)
            error_dia.ShowModal()
            error_dia.Close()
        if not exists(execVal):
            error_dia = wx.MessageDialog(self, "Under \"Paths\" tab\n\nExecutables folder does not exists",
                                         "Directory Error", wx.OK|wx.ICON_ERROR)
            error_dia.ShowModal()
            error_dia.Close()
        if self.optfiles_widg.IsEnabled() and optfilesVal == "":
            error_dia = wx.MessageDialog(self, "Under \"Paths\" tab\n\nOptional Files directory cannot be blank",
                                     "Directory Error", wx.OK|wx.ICON_ERROR)
            error_dia.ShowModal()
            error_dia.Close()
        if not exists(destVal):
            error_dia = wx.MessageDialog(self, "Under \"Build\" tab\n\nDestination folder does not exists",
                                         "Directory Error", wx.OK|wx.ICON_ERROR)
            error_dia.ShowModal()
            error_dia.Close()
        else:
            try:
                os.mkdir("%s/%s_tmp" % (destVal,nameVal))
            except OSError:
                pass
            
            # --- Making the directory tree
            if self.xout_bin.GetValue() == True:
                if exists("%s/bin" % treeVal):
                    print "Executables path already exists"
                else:
                    print "Creating directory %s/bin" % treeVal
                    os.mkdir("%s/bin" % treeVal)
...
...
...
[/php]
I can't see where I've gone wrong.  Shouldn't the else statement only execute if the other statements have not been satisfied?

---

### Post by dandaman0061 on 2009-05-16
Well firstly you have 2 'else' statements, but I'm assuming you mean the first one keeps executing.

Your desired flow requires elif statements instead of 'if' below the first:

```

if x:
   pass
elif y:
   pass
elif z:
   pass
else:
   pass

```

---

### Post by dodle on 2009-05-16
Yes, I meant the first, sorry.  I didn't realize that the elif statements were required.  I've heard that using a lot of [color=red]if[/color]/[color=red]elif[/color] statements is not good OO programming.  Should I try to find another way to do this?

---

### Post by k2t0f12d on 2009-05-16
> **dodle said:**
> Yes, I meant the first, sorry.  I didn't realize that the elif statements were required.  I've heard that using a lot of [color=red]if[/color]/[color=red]elif[/color] statements is not good OO programming.  Should I try to find another way to do this?If it works, who cares?  Don't retard your programming skills to win approval from some priest of the church of OO.

---

