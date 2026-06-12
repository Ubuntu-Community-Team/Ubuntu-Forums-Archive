---
title: "Simple BASH question"
date: 2012-02-08
forum: Programming Talk
---

### Post by partloer on 2012-02-08
Just trying to create a simple BASH script that the main.sh file calls a function in the def.sh file.

main.sh
```
#!/bin/bash
./def.sh
test
exit
```
def.sh
```
test(){
    echo "test"
}
```

I run "sh main.sh" and get no output.  I tried Googling this but couldn't find anything as to why the file is included but the function call doesn't work.

---

### Post by MadCow108 on 2012-02-08
written like this it does not include the other file but executes the file in another process. it then has no influence on the current file

to include you have to use
```
. def.sh
```
(note the space after the dot) or
```
source def.sh
```

---

### Post by partloer on 2012-02-09
I have tried this before.

```
source def.sh
```However I get an error.  

```
main.sh: 3: source: not found
```

The file is in the same folder and I have tried absolute paths too.

---

### Post by partloer on 2012-02-09
BAM!...it works, thanks Major_Bloodnok

---

### Post by Khayyam on 2012-02-09
partloer ...

Set 'bash' rather than 'sh' as the interpreter, 'sh' doesn't have the 'builtin' source. Also 'test' is a unix command, so choose something unique as the function identifier.

Main.sh
```
#!/bin/bash

source $(pwd)/def.sh

testit

exit
```def.sh
```
function testit()
{
    echo "test"
}
```run the test ..
```
% chmod u+x main.sh
% ./main.sh
test
```

---

