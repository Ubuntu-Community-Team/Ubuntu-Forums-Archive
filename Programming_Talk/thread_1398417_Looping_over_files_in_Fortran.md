---
title: "Looping over files in Fortran?"
date: 2010-02-04
forum: Programming Talk
---

### Post by jsmidt on 2010-02-04
Hey,  i've learned a bunch of for fortran but have yet to read how to loop over files like this:

I have 100 files called myfile_1_1.txt, myfile_1_2.txt,...,myfile_10_10.txt with two columns of numberse.

How would I code (this is pseudo code)

```

do i = 1, 10
  do j = 1, 10
    
    read("myfile_"+i+"_"+j+".txt") x, y

  end do
end do

```

So anyways, if anyone could tell me how to write the above to loop over the file, ie, get read to know that if i = 4 and j = 5 to read file myfile_4_5.txt, that would be helpful.  Thanks.

---

### Post by Maz_ on 2010-02-04
```

PROGRAM testaus
  IMPLICIT NONE
  INTEGER :: i,j
  CHARACTER(LEN=*), PARAMETER :: filebase = "myfile_"
  CHARACTER(LEN=*), PARAMETER :: fileend = ".txt"
  CHARACTER(LEN=20) :: filename
  INTRINSIC SIN

  DO i=1,100
    DO j=1,100
      WRITE(filename,'(A,I3.3,A,I3.3,A)') 'myfile_',i,'_',j,'.txt'
      WRITE (*,*) filename
    END DO
  END DO
END PROGRAM testaus

```

Replace latter WRITE with OPEN.

---

