---
title: "in python is there a way to round a floating point number to the second decimal place"
date: 2007-08-01
forum: Programming Talk
---

### Post by luckyd on 2007-08-01
So is there?

---

### Post by kebes on 2007-08-01
To round things, use the "round" function. It takes two arguments, the number to round and the number of decimal places you want. For example:

```

a = 2.3456
b = round(a, 2)
print b

```

Would print out:
2.35

---

### Post by luckyd on 2007-08-01
thank you

---

### Post by luckyd on 2007-08-01
i spoke too soon, now it is complaining about invalid syntax, please take a look at this code to find free harddrive space and see what it wrong. 
> elif self.disk_value == "free space":
	         disk_space = [(float(free)/1048576)]
		 disk_space = (str(round(disk_space, 2))
		  return [disk_space + " GB free", mountpoint]

it says
>  File "/home/hayden/.screenlets/Systemstatus/SystemstatusScreenlet.py", line 227
    return [disk_space + " GB free", mountpoint]
            ^
SyntaxError: invalid syntax

except that the arrow is actually on the n in return, i cant get it to line up on the forums

---

### Post by kebes on 2007-08-01
On your second-to-last line you open three parentheses but only close two. So this:

disk_space = (str(round(disk_space, 2))

Should presumably be:

disk_space = (str(round(disk_space, 2)))

(add a closing bracket on end)

---

### Post by luckyd on 2007-08-01
Ok, I was really stupid when I missed that, but it didn't fix the problem.
I'll start from the beginning with what I am trying to do, becuase otherwise I dont know how to explain it. I have been messing with the system status screenlet, and have been making some changes. One of those was that when it displayed free harddrive space I wanted it display in gigabytes instead of megabytes. However when I tryed to do this it displayed the amount of gigabytes and then about 15 digits after the decimal place(since I made it a float).
When I followed your instructions, the screelet popped up but with no information of anykind on it. When I turned the harddrive space option off altogether, than all the other information popped up again. I have posted up the working screenlet, with the longlist of number after the decimal. If anyone has any idea about what im doing wrong, please help. All you have to do once you install the screenlet, to view the harddrive space data is enter the directory of your disk under the screenlet's properties :)

P.S. It's for screenlets .0.0.7

---

### Post by cwaldbieser on 2007-08-02
> **luckyd said:**
> Ok, I was really stupid when I missed that, but it didn't fix the problem.
I'll start from the beginning with what I am trying to do, becuase otherwise I dont know how to explain it. I have been messing with the system status screenlet, and have been making some changes. One of those was that when it displayed free harddrive space I wanted it display in gigabytes instead of megabytes. However when I tryed to do this it displayed the amount of gigabytes and then about 15 digits after the decimal place(since I made it a float).
When I followed your instructions, the screelet popped up but with no information of anykind on it. When I turned the harddrive space option off altogether, than all the other information popped up again. I have posted up the working screenlet, with the longlist of number after the decimal. If anyone has any idea about what im doing wrong, please help. All you have to do once you install the screenlet, to view the harddrive space data is enter the directory of your disk under the screenlet's properties :)

P.S. It's for screenlets .0.0.7
I run Kubuntu, so I couldn't test this for you, but you could just change the line:
```

data = commands.getoutput("df | grep " + self.disk_name)

```
to
```

data = commands.getoutput("df -B 1G | grep " + self.disk_name)

```
That will cause the "df" command to output the sizes in 1G units.

---

