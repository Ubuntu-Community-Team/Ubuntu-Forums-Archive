---
title: "Help with License??"
date: 2008-12-02
forum: Packaging and Compiling Programs
---

### Post by Tamalin on 2008-12-02
I am trying to figure out how to use software licenses on my software, but I'm not sure exactly how to comply to the liscenses.  I had chosen the Apache Liscense, but their site seems to indicate that this liscense is for code developed at Apache Software Foundation.  None of my code was ever developed at Apache Software Foundation, and I was wondering if I could still use the Liscense on any code.  I'm also very unclear on how I should work the liscense.  I need to know what to put in the NOTICE file and the LICENSE file, any other files I need to include, and where I put the files.
Can anyone help me?  Thank You.

---

### Post by ggaaron on 2008-12-13
You do this exactly as the license appendix says:
[http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)
You copy this license to a LICENSE or COPYING file and in every file you have you put a notice:
 Copyright [yyyy] [name of copyright owner]

 Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

 [http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)

 Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.

And that's all. Remember though that Apache license is not GPL-2 compatible if you'd like to use GPL-ed code.

---

### Post by Tamalin on 2008-12-13
Ok, that's good to know...  Thank You.
But I was still wondering, what is in the "Notice file" & what are "Attribution Notices", & how exactly do I create them?

Thanks!

---

### Post by ggaaron on 2008-12-13
If the work is not your own then you have to include a file where all original developers will be listed. It only applies if you take an already Apache licensed project and change it.

---

### Post by Tamalin on 2008-12-13
Ok, that's what I wanted.  Can I create my own "NOTICE" file?

---

### Post by ggaaron on 2008-12-13
It is a plain text file=)
Read point 4. Redistribution of the license again - it says that you may have this file but you don't have to and there you should put any attribution - names of people that contributed to your project, or names of people whose code you've taken and put into your work.

---

### Post by Tamalin on 2008-12-13
Ok, is there a certain format I have to put the name/attributions in for NOTICE, or can I just list whatever I want in the file?

---

### Post by ggaaron on 2008-12-13
It's up to you I think.

Happy hacking=)

---

### Post by Tamalin on 2008-12-13
Ok, thank you so much!

What should I do to my documentation, do I need to include anything there?  I am using javadoc.

---

### Post by ggaaron on 2008-12-13
You should license documentation as well, I don't remember if javadoc has a license tag, if not and you can't do it easily then a note in top folder of doc saying something like: "This is documentation of project X, everything in this directory and it's subdirectories is licensed under Y license.". Put also a link to the license, copyright notes, probably license header and it should be enough.

---

### Post by Tamalin on 2008-12-13
Ok, Thank You!

---

