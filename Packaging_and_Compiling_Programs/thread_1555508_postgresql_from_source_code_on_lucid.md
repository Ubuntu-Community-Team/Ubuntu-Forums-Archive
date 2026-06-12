---
title: "postgresql from source code on lucid"
date: 2010-08-18
forum: Packaging and Compiling Programs
---

### Post by SteelCore on 2010-08-18
I'm trying to install PostgreSQL 8.4.4 from source code onto freshly installed and updated Lucid. After extracting source code and running ./configure I got 3 error messages regarding missing bison, flex and readline libraries. I managed to install the first 2 from synaptic but for the 3rd there is a 'readline-common' that is already installed. I ran './configure' again and first 2 errors are gone but the readline library error is still there and it states that if it is already installed the program might not be looking in the right place, though I don't know how to fix this. Thank you for any help.

---

### Post by SevenMachines on 2010-08-18
its probably libreadline-dev you're looking for

---

### Post by SteelCore on 2010-08-18
Thanks, that did remove the error. Then a new one came up (zlib library not found). In Synaptic, there was a 'zlib1g' that's already installed but a 'zlib1g-dev' which wasn't. Following the same logic, though I dont really understand why, I installed it. The last run of ./configure took much longer but doesn't seem to have resulted in any errors.

---

### Post by SevenMachines on 2010-08-18
In general when ./configure complains 
something.... not found

you're usually looking for, in order of likelihood
 
* libsomething-dev
* something-dev

although there are a few cases, like bison as you mention, where its not a -dev package. Theres not an obvious way to tell, just painful experience of staring at millions of them over time :)

---

### Post by SteelCore on 2010-08-18
> **SevenMachines said:**
> ...Theres not an obvious way to tell, just painful experience of staring at millions of them over time :)

For the resulting gain, it's well worth the effort :)

---

