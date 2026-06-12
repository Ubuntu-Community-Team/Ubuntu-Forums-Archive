---
title: "[SOLVED] Runtime Error : Conflicting Statement Options"
date: 2008-08-27
forum: Programming Talk
---

### Post by lordhaworth on 2008-08-27
Hey all
Another obstacle in my learning of Fortran90 has been getting in the way for a while and I cant find a way to resolve it! 
I have two programs now which are being hindered by problems when reading from an external file. 
The file opens fine and in the past I have written programs which read only one line of data, but when I try to read a whole document of more than one line it screws up. I checked the runtime error code is 200 (for compiler g95) which means **"Conflicting Statement Options". **Does anyone know what this means? 

I cant post code from these programs until this evening, but my code for reading from the file is roughly (off the top of my head)

```

DO
  READ(1, IOSTAT = ReadStatus), Rank, Name, Score
  IF (ReadStatus < 0) EXIT
  ELSE IF (ReadStatus > 0) THEN
      PRINT *, "Runtime Error :" ReadStatus
      STOP
  END IF
END DO

```


Thanks For Any Help

Tom

---

### Post by lordhaworth on 2008-08-29
For anyone whose interested, it was a simple syntax error

```

READ(1, *, IOSTAT = ReadStatus), ...

```

Instead Of

```

READ(1, IOSTAT = ReadStatus), ...

```

Im assuming that second bit (in the correction marked with , *,)
must be reserved for some other specifier - actually i think it might be formatted reading.

---

