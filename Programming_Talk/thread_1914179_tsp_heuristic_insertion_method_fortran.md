---
title: "tsp heuristic insertion method fortran"
date: 2012-01-23
forum: Programming Talk
---

### Post by Claus7 on 2012-01-23
Hello,

is there someone that has dealt with the travelling salesman problem and especially with:

[LIST]
[*]euclidean (x,y coordinates)
[*]heuristic
[*]insertion method
[*]fortran
[/LIST]

code/algorithm?

I was able to find insertsort subroutine, yet this sorts out an array that has only one dimension. What is going to happen if the distance between two different points is going to be the case?

Any information or link will be most welcome!

Thank you,
Regards!

---

### Post by Bachstelze on 2012-01-23
I did a project last year in school that implemented that. It's in C, though (and commented in French), but if you are interested, the code is on my WebSVN.

[http://svn.fkraiem.org/listing.php?repname=inf255](http://svn.fkraiem.org/listing.php?repname=inf255)

---

### Post by Claus7 on 2012-01-24
Hello,

> **Bachstelze said:**
> I did a project last year in school that implemented that. It's in C, though (and commented in French), but if you are interested, the code is on my WebSVN.

[http://svn.fkraiem.org/listing.php?repname=inf255](http://svn.fkraiem.org/listing.php?repname=inf255)

thank you so much for your prompt response, yet I have to admit that right now I have a problem adjusting with c. I was able to find about your project under (root)/src/tsp_insertion.c. Very good organization, thank you for your feedback.

Regards!

---

### Post by Claus7 on 2012-01-25
Hello,

just a pseudo-code for the problem:

```
!	Sorting coordinates	

	temporary2 = maxval(of distances given)

	i = 1
	j = i + 1
	jj= 1
	do while (distance(i,j) < dist_reference .and. temporary1 .ne. 10**8.d0)
		
		do i = 1, number_of_cities -1

		   do j = i+1, number_of_cities 

		   if (distance(i,j) .le. dist_reference .and. distance(i,j) .gt. 0.d0) then
			dist_reference = distance(i,j)
			if (dist(i,j) .eq. temporary1) then

			distance(i,j) -> neglect it
			endif
		   endif

		   enddo
		
		enddo

		route = dist_reference + route

		dist_reference = 10**8.d0

		i = 1
		j = i + 1
		jj= jj+ 1
	enddo ! do while
```

EDIT: If we would like to visit every point only once, this procedure is NOT sufficient

Regards!

---

