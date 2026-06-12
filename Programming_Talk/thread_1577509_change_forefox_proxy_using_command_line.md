---
title: "change forefox proxy using command line"
date: 2010-09-19
forum: Programming Talk
---

### Post by vksingh on 2010-09-19
Hi,


How to change firefox proxy using command line in ubuntu.

Thanks,

Vivek

---

### Post by kurum! on 2010-09-19
```

#!/usr/bin/env ruby -w
home=File.expand_path("~")
found=""
Dir.glob("#{home}/**/prefs.js", File::FNM_DOTMATCH).each do  |file|
   found<<file if file =~ /firefox.*default\/prefs.js$/
end
newproxy = '"new.proxy.com");'
newfile = File.open("temp", "w")
File.open(found).each do |line|
  if line =~ /network.proxy.http/
     x,y = line.chomp.split(", ")
     line=[x,newproxy].join(", ")
  end
  newfile.print line
end
newfile.close
File.rename(found, "old.orig")
File.rename("temp", found)


```

---

### Post by vksingh on 2010-09-20
> **kurum! said:**
> ```

#!/usr/bin/env ruby -w
home=File.expand_path("~")
found=""
Dir.glob("#{home}/**/prefs.js", File::FNM_DOTMATCH).each do  |file|
   found<<file if file =~ /firefox.*default\/prefs.js$/
end
newproxy = '"new.proxy.com");'
newfile = File.open("temp", "w")
File.open(found).each do |line|
  if line =~ /network.proxy.http/
     x,y = line.chomp.split(", ")
     line=[x,newproxy].join(", ")
  end
  newfile.print line
end
newfile.close
File.rename(found, "old.orig")
File.rename("temp", found)


```


Hi, 

Thanks for your help.
I tried to run your script but, I am getting following error:

***/usr/bin/env: ruby -w: No such file or directory***


Please help.

Thanks,

Vivek

---

### Post by kurum! on 2010-09-20
you have to install ruby if you want to use the script. otherwise, wait for someone else for alternative

---

