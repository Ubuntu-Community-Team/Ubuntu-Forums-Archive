---
title: "ARM linker fail"
date: 2012-06-30
forum: Programming Talk
---

### Post by bogdanul2003 on 2012-06-30
[LEFT]I'm trying to compile RTEMS for a STM32F4DISCOVERY board. Everything  goes well until the linker tries to find the linker script  linkcmds.armv7m. I searched for the file on my system and I found it  some places.  /opt/rtems-4.11/bin/ld/linkcmds.armv7m /opt/rtems-4.11/arm-rtemseabi4.11/lib/linkcmds.armv7m find: `/home/boil/.gvfs': Permission denied /home/boil/Documents/b-rtems/arm-rtemseabi4.11/gumstix/lib/linkcmds.armv  7m /home/boil/Documents/arm-work/rtos/c/src/lib/libbsp/arm/shared/startup/l  inkcmds.armv7m /home/boil/Documents/arm-work/base_sp2/linkcmds.armv7m /home/boil/Documents/arm-work/lib/linkcmds.armv7m /home/boil/Documents/arm-work/bin/arm-rtemseabi4.11/stm32f4/lib/linkcmds  .armv7m /home/boil/Documents/rtems/c/src/lib/libbsp/arm/shared/startup/linkcmds.  armv7m   And this is the last output when trying to comppile RTEMS  arm-rtemseabi4.11-gcc -Os -B ./../bin/arm-rtemseabi4.11/stm32f4/lib/  -specs bsp_specs -qrtems -mstructure-size-boundary=8 -march=armv7-m  -mthumb -fno-schedule-insns2 -fno-common -O0 -g3 -ggdb -g -Wall  -Wmissing-prototypes -Wimplicit-function-declaration  -mstructure-size-boundary=8 -march=armv7-m -mthumb -fno-schedule-insns2  -fno-common -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1  -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_STRINGS_H=1  -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_CSTDIO=1  -DHAVE_CSTDLIB=1 -DHAVE_IOSTREAM=1  -I./../bin/arm-rtemseabi4.11/stm32f4/lib/include -I./inc  -g  -Wstrict-prototypes -Wnested-externs ./obj/stm32f4_discovery.o  ./obj/stm32f4xx_exti.o ./obj/init.o ./obj/stm32f4xx_rcc.o ./obj/misc.o  ./obj/stm32f4xx_syscfg.o ./obj/apptask.o -o elf/base_sp.elf /opt/rtems-4.11/lib/gcc/arm-rtemseabi4.11/4.7.1/../../../../arm-rtemseab  i4.11/bin/ld:  cannot open linker script file linkcmds.armv7: No such  file or directory collect2: error: ld returned 1 exit status make: *** [elf/base_sp.elf] Error 1  Can you tell how to fix this?[/LEFT]

---

### Post by Zugzwang on 2012-06-30
Can you please format your post in a readable way?

---

### Post by bogdanul2003 on 2012-06-30
Sorry for that :)

> **bogdanul2003 said:**
> [LEFT]I'm trying to compile RTEMS for a STM32F4DISCOVERY board. Everything  goes well until the linker tries to find the linker script  linkcmds.armv7m. I searched for the file on my system and I found it  some places.

 /opt/rtems-4.11/bin/ld/linkcmds.armv7m
 /opt/rtems-4.11/arm-rtemseabi4.11/lib/linkcmds.armv7m
/home/boil/Documents/b-rtems/arm-rtemseabi4.11/gumstix/lib/linkcmds.armv  7m
/home/boil/Documents/arm-work/rtos/c/src/lib/libbsp/arm/shared/startup/l  inkcmds.armv7m
/home/boil/Documents/arm-work/base_sp2/linkcmds.armv7m 
/home/boil/Documents/arm-work/lib/linkcmds.armv7m
 /home/boil/Documents/arm-work/bin/arm-rtemseabi4.11/stm32f4/lib/linkcmds  .armv7m
 /home/boil/Documents/rtems/c/src/lib/libbsp/arm/shared/startup/linkcmds.  armv7m 


And this is the last output when trying to comppile RTEMS  

arm-rtemseabi4.11-gcc -Os -B ./../bin/arm-rtemseabi4.11/stm32f4/lib/  -specs bsp_specs -qrtems -mstructure-size-boundary=8 -march=armv7-m  -mthumb -fno-schedule-insns2 -fno-common -O0 -g3 -ggdb -g -Wall  -Wmissing-prototypes -Wimplicit-function-declaration  -mstructure-size-boundary=8 -march=armv7-m -mthumb -fno-schedule-insns2  -fno-common -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1  -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_STRINGS_H=1  -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_CSTDIO=1  -DHAVE_CSTDLIB=1 -DHAVE_IOSTREAM=1  -I./../bin/arm-rtemseabi4.11/stm32f4/lib/include -I./inc  -g  -Wstrict-prototypes -Wnested-externs ./obj/stm32f4_discovery.o  ./obj/stm32f4xx_exti.o ./obj/init.o ./obj/stm32f4xx_rcc.o ./obj/misc.o  ./obj/stm32f4xx_syscfg.o ./obj/apptask.o -o elf/base_sp.elf /opt/rtems-4.11/lib/gcc/arm-rtemseabi4.11/4.7.1/../../../../arm-rtemseab  i4.11/bin/ld:  cannot open linker script file linkcmds.armv7: No such  file or directory collect2: error: ld returned 1 exit status make: *** [elf/base_sp.elf] Error 1

 Can you tell how to fix this?[/LEFT]


---

