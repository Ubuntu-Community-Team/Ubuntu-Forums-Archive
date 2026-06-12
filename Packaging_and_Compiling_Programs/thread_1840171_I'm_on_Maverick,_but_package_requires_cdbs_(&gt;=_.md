---
title: "I'm on Maverick, but package requires cdbs (&gt;= 0.4.85~)"
date: 2011-09-07
forum: Packaging and Compiling Programs
---

### Post by Gias Kay on 2011-09-07
Hello all,

I am trying to update and repackage a program, whose original control file states that it requires cdbs (>= 0.4.85~) as a build dependency; however I am on Maverick whose [cdbs]("https://launchpad.net/ubuntu/+source/cdbs") only goes as far as v0.4.83ubuntu2.

Is there any reliable/official Ubuntu PPA offering a more up-to-date version of cdbs for Maverick, so I can list that as a build dependency inside my own PPA? Or is it safe to specify a slightly older version of cdbs for the job - in this case, downgrade the requirement to cdbs (>= 0.4.83~)? Or any other way I can have it successfully built on Maverick?

Thanks for your help!

---

### Post by gmargo on 2011-09-07
Since you don't even mention what software you are trying to package, it is impossible to help.  No one can say if it's ok to downgrade a requirement for a mystery package.

If you want to search the PPA space to find if anyone has provided a later version of <insert package here>, you should use the PPA search at [https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

---

