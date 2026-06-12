---
title: "Confirming gfortran bug (launchpad #1330099)"
date: 2014-08-29
forum: Packaging and Compiling Programs
---

### Post by Miguel on 2014-08-29
Dear ubuntu baristas,

Ever since I upgraded my ubuntu machines to 14.04, I've been affected by a gfortran bug, which renders it completely unusable by some software packages I use in a day to day basis. It's reported in launchpad ([#1330099](https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/1330099)), and gcc-bugcilla ([#61173](https://gcc.gnu.org/bugzilla/show_bug.cgi?id=61173)). Actually, as a matter of fact, it's confirmed, has a patch and has been fixed in gcc for 4.9.1. Given that I reported this ages ago, that it has a fix upstream, that the bug only appears in the Trusty branch of gcc 4.8.2 due to the Ubuntu/Debian patchset, it annoys me that no one has bothered replying to that bug. 

So if you have a bit of time, and gfortran installed, could you please try to compile and run the testcase? And then comment on launchpad? The gfortran testcase is in the first comment of the gcc bugzilla report, but I'll put it here as well:
```

module bd
  character(len=256), dimension(:), allocatable, save :: source
  contains
    subroutine init_data

      allocate(source(3))
      deallocate(source)

      allocate(source(2))

      source=["   1   1   1","   4   4   4"]

    end subroutine init_data
end module bd
program read_internal

  use bd

  integer :: x(6),i,iostat
  character(len=512) :: iomsg

  call init_data

  read(source,*,iostat=iostat,iomsg=iomsg) (x(i), i=1,6)
  if( iostat /= 0 ) then
     write(*,*) "Error: ",trim(iomsg)
  else
     write(*,*) (x(i), i=1,6)
  end if
end program read_internal

```

Thank you!

---

