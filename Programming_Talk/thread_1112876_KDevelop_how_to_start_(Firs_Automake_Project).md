---
title: "KDevelop how to start (Firs Automake Project)"
date: 2009-04-01
forum: Programming Talk
---

### Post by yoni_m on 2009-04-01
Hi all,

This is my first "tutorial" post and I hope this it the correct place to post it, if not i trust someone will move it to a better place.

So here goes...

KDevelope is suppose to be nice to work in but I found it hard to start my firs Automake project. After MUCH trial and even more error (and lots of www help) I think I've got it. The algorithm follows:

1. Fire up "KDevelop: C/C++".

2. Choose Project
            |
            -> New Project
                 |
                 -> C++
                     |
                      -> Automake Project
                          |
                          -> Empty Automake template
/* Do not be alarmed you are not expected to write the template */

3. Make sure that the location (path) for the project is a Linux disk. You can not compile of non-Linux disks you will get error to the efect that there is some kind of perditions issue.

4. Give the project a name.

5. Hit Next ... Next ... Finish /* In the future you might want to change things on the way but for now just go through the next next procedure.

6. Now you get an alarming pop-up ignore it and just hit Ok /* If you actually read it the content will through you of the trail. It is beyond me why this pops up at this point and why the content is so confusing */

7. On the right find the Automake manager if it is not open open it.

8. In the Automake manager just over the top part you will see 4 buttons. One of them (the second from the left) will create a new target (the tool tip says "Add target"). Hit that one.

9. In the pop up give the target a name.

10. Only now do you have a target!!! It should appear in the bottom half of the Automake manager.

11. Right click the newly created target (in the bottom part of the Automake manager).

12. Choose "Make target Active". The target should turn bold.

13. Right click the target again.

14. Choose create new file.

15. Give the file a name, make sure it is of the type you need (h cpp) and make sure that "add to project" is selected.

16. Now you get another useless pop up. Ignore it.

17. Choose you new file from the list below and hit Ok.

18. On the right the file should be added to the list of your files (if you can not see it hunt around, you can use the "File group" tab on the left...)

19. Add code to the file e.g.:

# include <iostream>

int main()
{
	std::cout<<"This  mutch to long and complicated can they not make it easer?"<< std::endl;

	return 0;
}

20. save the file.

21. Now you can compile you project....

21a. if you just run it KDevelope will do everything.

21b. run Automake & friends from the Build menu.


22. Write a program to save the world and post it for free on the net.


Enjoy

Yoni
[http://www.cs.huji.ac.il/~yoni_m/index.html](http://www.cs.huji.ac.il/~yoni_m/index.html)

---

### Post by Swerve1000 on 2009-10-18
Does this look like it would work?

The lack of comments and the date it was posted makes me kinda suspicious.

---

### Post by yoni_m on 2009-10-25
Sorry for the lack of comments, but it is a simple list of actions.
You can be suspicious or you could give it the 5 minutes it takes and try it.
It works for me.
I do not see what there is to be suspicious of. Do you think it might harm you or your computer?
Please try it and let me know what you think then.

---

### Post by monster on 2009-10-26
Hi,
Thanks for tutorial.
I added some more files(from existing project) and I have errors like:
Makefile:[linenumber]:.deps/air.Po: No such file or directory.

What can I do about that?

---

### Post by yoni_m on 2009-10-27
Hi,
It is not clear how you added the files. Did you only copy them to the folder, did you add them to the project etc. The simplest (not necessarily the best) way is to copy the files to the new project folder and then add them to the project.

---

