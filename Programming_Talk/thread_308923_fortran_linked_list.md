---
title: "fortran linked list"
date: 2006-11-28
forum: Programming Talk
---

### Post by macsaint on 2006-11-28
Hello

I am making a linked list code. The result should be as

1.0
2.0

But it shows the result as

0.0
1.0
2.0

I don't know where the zero value comes from. :confused: 

Plz, help me

JW



C=========================================
module list
******************************************
type :: list_node
type (list_node), pointer :: p
real(8) :: data
end type list_node
******************************************
end module list

subroutine list_test(n,head)
use list
type (list_node), pointer :: tail, head, ptr
integer :: i, n
integer :: istatus

n = 2

do i = 1, n
if (i.eq.1) then
allocate(head,stat=istatus)
tail => head
else
allocate(tail%p,stat=istatus)
tail => tail%p
end if

tail%data = i
nullify(tail%p)

end do
end subroutine list_test

******** MAIN PROGRAM ******
program test
use list
type (list_node), pointer :: head, ptr
integer :: n

allocate(head,stat=istatus) ! important
call list_test(n,head)

ptr => head

istatus = associated(ptr)

do while ( associated(ptr) )
print *, 'data=', ptr%data
ptr => ptr%p
end do

end program test

---

### Post by junglepeanut on 2006-11-29
I saw this and I had never heard of it before and this looked interesting so I read your code. Looked up the names and could not recognize the issue. So I built my own, first as just a program and then took it apart piece by piece compiling at each point. I still could not figure out the issue (4 and a half hours later), so I fell back on the something that has never let me down, the ability for a module to catch many errors. I use this whenever I get really lost. Guess what it worked and made me think until it dawned on me that in making the subroutine non-global Fortran may create a dummy to speed up process or something (I really don't know but that is what I was guessing.) Then I searched on the Internet for something similar to what we were seeing and pow =>

[http://www.cs.rpi.edu/~szymansk/OOF90/bugs.html#6](http://www.cs.rpi.edu/~szymansk/OOF90/bugs.html#6)

 So it appears that you are losing a pointer as it gets crushed for speed, if I read correctly. Therefore sort of like declaring a target we need to make sure that the pointer stays where we need it. So here is my code before it got destroyed by cutting it to pieces (looked horrible after cut and pasting) to put in a form similar to yours. ( I have to show it off because it has the longest variable names I have ever made so that I could solve this problem. I mostly do numerical work and just use simple variable names, like x.) ```

Module module_of_linked_list
Implicit None

	Type :: something

		Real :: values_of_something
		Type (something), Pointer :: points2something

	End Type

End Module module_of_linked_list


Program myfirstlinkedlist
Use module_of_linked_list
Implicit None

	Type (something), Pointer :: points2head_of_something, points2butt, temporary_pointer
	Integer :: istatus, indx

	get2numbers : Do indx=1,2,1

		question_top : If ( indx == 1) then
	 
			allocate (points2head_of_something, stat=istatus)
			points2butt => points2head_of_something

		Else

			allocate (points2butt%points2something, stat=istatus)
			points2butt => points2butt%points2something

		End If question_top

		nullify (points2butt%points2something)
		points2butt%values_of_something = real(indx)

	End Do get2numbers

	temporary_pointer => points2head_of_something

	what_we_got : Do while (associated(temporary_pointer))

		Write(*,*) temporary_pointer%values_of_something
		temporary_pointer => temporary_pointer%points2something

	End Do what_we_got

End Program myfirstlinkedlist

```
Here is your code with the simple fix
```

module list

type :: list_node
type (list_node), pointer :: p
real(8):: data
end type list_node
Contains
subroutine list_test(n,head)
type (list_node), pointer :: tail, head, ptr
integer :: i, n
integer :: istatus

n = 2

do i = 1, n
if (i.eq.1) then
allocate(head,stat=istatus)
tail => head
else
allocate(tail%p,stat=istatus)
tail => tail%p
end if

tail%data = i
nullify(tail%p)

end do
end subroutine list_test

end module list



program test
use list
type (list_node), pointer :: head, ptr
integer :: n

allocate(head,stat=istatus) ! important
call list_test(n,head)

ptr => head

istatus = associated(ptr)

do while ( associated(ptr) )
print *, 'data=', ptr%data
ptr => ptr%p
end do

end program test

```

---

### Post by macsaint on 2006-11-29
Hello

Thank you for your help.
Is it possible to have a separate subroutine?

JW

---

### Post by junglepeanut on 2006-11-29
I don't know how, but maybe you can get more understanding from the link than I did. The link says some reasons why this is this way.

---

