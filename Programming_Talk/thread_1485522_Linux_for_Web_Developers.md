---
title: "Linux for Web Developers"
date: 2010-05-16
forum: Programming Talk
---

### Post by techrush on 2010-05-16
I recently did a couple blog posts on using linux for web development. Since my distro of choice is Ubuntu and has been since around 5.10 i thought i'd share it with you guys. Wouldn't have been able to get to where i am with it without the help of the people on the forums here. Especially in the early days

That being said these are the 1st two parts of a series of posts on the topic. I won't be discussing coding too much but just outlining the apps and workflow needed to do web development on linux.

My goal is to help good web developers who are new to linux find the apps they need and show them that the workflow is manageable and actually highly
productive with a little practice.

If anyone has any questions about web development under ubuntu i'll do my best to answer them here or in the comments of the blog. Thanks!

Part I - Overview: [http://adamctemple.com/blog/linux-for-web-development](http://adamctemple.com/blog/linux-for-web-development)
Part II - Server Side Tools: [http://adamctemple.com/blog/linux-for-web-development-server-side-tools/](http://adamctemple.com/blog/linux-for-web-development-server-side-tools/)

---

### Post by lykwydchykyn on 2010-05-16
second link is bad.

Should be: [http://adamctemple.com/blog/linux-for-web-development-server-side-tools/](http://adamctemple.com/blog/linux-for-web-development-server-side-tools/)


I think it's pretty interesting seeing how other people get work done, what kind of tools they assemble to accomplish a job.  I think that's part of the culture shock for people moving from the commercial proprietary platform realm to the FOSS realm -- we don't have the big monolithic do-it-all software packages.  You don't just run out and buy Dream Weaver because that's what Everyone Runs (TM), you assemble a set of tools that suit you.

I want to add a comment on the second article: as an alternative to linking /var/www to ~/Desktop, you can enable the userdirs module in apache.  This will publish anything in a user's ~/public_html directory to [http://server/~username/](http://server/~username/).  Very convenient on a shared development server.

Of course, it's  matter of personal preference.

---

### Post by techrush on 2010-05-18
Fixed the URL, thanks. I do agree with you about sharing your workflow. Just finding the right tools for the job was the biggest struggle for me in the beginning.

---

