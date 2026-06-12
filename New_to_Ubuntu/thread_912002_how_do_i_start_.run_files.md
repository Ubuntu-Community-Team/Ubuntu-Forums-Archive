---
title: "how do i start .run files?"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by Meow27 on 2008-09-06
errr. hey there


ive recently tormented that battlestar galactica demo (for linux which is a run file)
but i dont know how to open it. i installed dosbox not too long ago and it looks like its the program thats taking care of those files....... can anyone tell me how to get my system running it again?

thanks

---

### Post by linuxlizard on 2008-09-06
.run is a linux native, not dosbox (I think).

Try opening a terminal and sticking ./ or sh in front of the run file. One of those should get it to run.

(or maybe it's /. - can't remember for sure)

---

### Post by cb951303 on 2008-09-06
first make sure that it's executable.

```

chmod +x file.run

```

than 
```

sh file.run

```

---

### Post by Stenrad on 2008-09-06
Hi

Try this:-

1. Open up a terminal.
2. Cd to the directory that the program is in.
3. Then type ```
sh <insert Battlestar Gallactica program name you are trying to run here>
```
4. You should end up with the desired result. :-)

Hope that helps!

Stenrad.

---

### Post by ronnielsen1 on 2008-09-06
dosbox is only for dos games

---

### Post by Meow27 on 2008-09-06
i know dosbox works only with dos programs...but i didnt make the option where it would open run programs....i dont know why that happened but it doesnt matter anymore.. thanks guys :D

---

