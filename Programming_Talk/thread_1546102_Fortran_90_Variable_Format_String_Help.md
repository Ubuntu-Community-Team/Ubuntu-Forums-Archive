---
title: "Fortran 90 Variable Format String Help"
date: 2010-08-04
forum: Programming Talk
---

### Post by ngrieb on 2010-08-04
I have been having a problem with a Fortran 90 format statement, and it's really bugging me now. I have a number of variables that I want to print out, but the number is dependent on the users input (i.e. perhaps the user wants to print X, Y, Z and T or maybe just X, Y, and Z). I have been trying to use a format statement to write a format string like this:

111 FORMAT("'(",I1,"(2X,F8.4), 2X, I)'")
 
Then writing the number of variables I1 into the above string like:

WRITE(string_name,111) number_of_variables

and then attempted to write to a file like:

WRITE(file_out,string_name) x , y, z(1:number_of_variables)

but of course this doesn't work. I tried TRIM(ADJUSTL(string_name)) as well, but it also fails. I know there has to be an easier way to do this, because this seems ridiculous. If anyone could provide a better way of doing this or tell me what I'm missing it would be mush appreciated. Thanks.

---

