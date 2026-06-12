---
title: "compiling problem"
date: 2011-10-22
forum: Programming Talk
---

### Post by kuldeepee on 2011-10-22
this is my subroutine 
```

subroutine selfile(name)

  ! call Window dialog to select file

  use dfwin
  implicit none
type T_OPENFILENAME
integer :: lStructSize
integer :: hwndOwner
integer :: hInstance
integer :: lpstrFilter
integer :: lpstrCustomFilter
integer :: nMaxCustFilter
integer :: nFilterIndex 
integer :: lpstrFile
integer :: nMaxFile
integer :: lpstrInitialDir
integer :: lpstrTitle
integer :: Flags
integer :: lpstrDefExt
integer :: lpfnHook
integer :: lpTemplateName
integer :: nMaxFileTitle
end type T_OPENFILENAME
  
  
  type(T_OPENFILENAME):: ofn
  character*100 filter_spec
  character*512 file_spec
  integer status
  character*(*)name

  ! set filter specification and string to return the file specification.

  file_spec=''C
  filter_spec = 'Data Files'C//'*.dat'C// &
                'Text Files'C//'*.txt'C// &
                'All files'C//'*'C//''C
  ofn%lStructSize = SIZEOF(ofn)
  ofn%hwndOwner = NULL
  ofn%hInstance = NULL
  ofn%lpstrFilter = loc(filter_spec)
  ofn%lpstrCustomFilter = NULL
  ofn%nMaxCustFilter = 0
  ofn%nFilterIndex = 1
  ofn%lpstrFile = loc(file_spec)
  ofn%nMaxFile = sizeof(file_spec)
  ofn%nMaxFileTitle = 0
  ofn%lpstrInitialDir = NULL
  ofn%lpstrTitle = loc('D Y N S I M'C)
  ofn%Flags = OFN_PATHMUSTEXIST
  ofn%lpstrDefExt = loc('dat'C)
  ofn%lpfnHook = NULL
  ofn%lpTemplateName = NULL

  ! Call GetOpenFileName and check status

  status = GetOpenFileName(ofn)
  if (status == 0) then
     name=''
  else
     name=file_spec
  endif
end subroutine selfile

```


i am getting these errors:---
```

Illegal use of constant "D Y N S I M"
 Illegal number or type of arguments to loc 
Illegal use of constant "dat"
Illegal number or type of arguments to loc 
Argument number 1 to getopenfilename: type mismatch
Illegal use of derived type
Illegal argument to %VAL or %LOC

```

---

### Post by mörgæs on 2011-10-22
Moved to Programming Talk.

---

### Post by gsmanners on 2011-10-22
Wow. Is that Fortran? Blast from the past.

---

