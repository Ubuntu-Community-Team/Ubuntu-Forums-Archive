---
title: "Group permissions"
date: 2011-12-26
forum: New to Ubuntu
---

### Post by SteveMHaupt on 2011-12-26
I hope this isn't a stupid question, but I have figured out several different ways to create users from the command terminal, can manipulate individual files permissions and users permissions. I can create groups and move users to and from them but I want to set default permissions for a group I create the apply to any user I place in that group and I just cant seem to find a  answer on line. Can someone help me. I've been bitten by the Linux bug and want so desperately to have a global understanding of it, and I'm hung up on this one thing, can somebody please give me a hand. I'm sure its very simple and I've probably overlooked in my desperate searching for the answer but as we all know sometimes one can be looking at the problem for so long the answer could be starring you right in the face. Thank you. 


Steven

---

### Post by Gone fishing on 2011-12-27
Not quite sure what you are asking but:

You can change group permissions using chgrp so you could place selected users into a group and then give a directory and its files ownership by that group (using the -R switch) and then chmod that directory (again using the -R switch) so that all group member could read and write to that directory and its files.

[http://www.freeos.com/node/48](http://www.freeos.com/node/48)

---

### Post by Lars Noodén on 2011-12-27
You'll probably also want to set the sticky bit for the group so that the permissions get passed on.

```

chmod g=rwxs ./some/dir/

```

---

