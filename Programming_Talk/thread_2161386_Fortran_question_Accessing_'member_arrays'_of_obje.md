---
title: "Fortran question: Accessing 'member arrays' of objects"
date: 2013-07-10
forum: Programming Talk
---

### Post by BramWillemsen on 2013-07-10
Hi,

Recently I have started using Fortran for a project, but I am relatively new to it. As part of the program I am writing, I have an object with an array member. Then I have a second object which needs to read this array. But I don't know how to do this efficiently. 

It seems like I cannot make an 'array member' of a class a TARGET. The code below doesn't compile for instance

```

MODULE t_obj_with_array
IMPLICIT NONE

  TYPE obj_with_array
    DOUBLE PRECISION, DIMENSION(:,:), ALLOCATABLE, TARGET       :: arraymember
  CONTAINS
    PROCEDURE, PUBLIC, pass                                     :: init => obj_with_array_init
    PROCEDURE, PUBLIC, pass                                     :: getarray => obj_with_array_getarray
  END TYPE obj_with_array

CONTAINS

  SUBROUTINE obj_with_array_init(t)
    IMPLICIT NONE
    CLASS(obj_with_array)                                       :: t
    ALLOCATE(t%arraymember(10,20))
  END SUBROUTINE obj_with_array_init

  FUNCTION obj_with_array_getarray(t)
    IMPLICIT NONE
    CLASS(obj_with_array)                                       :: t
    DOUBLE PRECISION, DIMENSION(:,:), POINTER                   :: obj_with_array_getarray
    obj_with_array_getarray => t%arraymember
    RETURN
  END FUNCTION obj_with_array_getarray

END MODULE t_obj_with_array

```

When I do "ifort -c t_obj_with_array.f90" I get the following result

```

t_obj_with_array.f90(5): error #6516: This attribute specification is not valid for a component definition statement.   [TARGET]
    DOUBLE PRECISION, DIMENSION(:,:), ALLOCATABLE, TARGET       :: arraymember
---------------------------------------------------^
t_obj_with_array.f90(23): error #6796: The variable must have the TARGET attribute or be a subobject of an object with the TARGET attribute, or it must have the POINTER attribute.   [T]
    obj_with_array_getarray => t%arraymember
-------------------------------^
compilation aborted for t_obj_with_array.f90 (code 1)

```

Is it possible to get read access to a member array without explicitly copying the array? I could write an accessor function that would access element (i,j) from the array, and return that. But I think that will cause some unnecessary overhead (when you enter the function, the stack pointer has to be incremented etc, unless there is a way to do things inline?)

Cheers!
Bram

EDIT: I guess writing an accessor function for element (i,j) might be most appropriate after all? I guess the compiler would make the function inline (as I cannot specify it like I would in C)

---

