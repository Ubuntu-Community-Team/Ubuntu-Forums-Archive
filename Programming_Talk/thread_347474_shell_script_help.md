---
title: "shell script help"
date: 2007-01-27
forum: Programming Talk
---

### Post by jaymode on 2007-01-27
Hi,

I do not know much about shell scripting and am trying to figure out why this one doesn't work. It was made automatically by a program to export some environment variables however it does not add them to the $PATH. It may be a simple fix. Here is the script:
```
PLATFORM=lin
XILINX_EDK=/video/microblaze/EDK/
export XILINX_EDK

if [ -n "$PATH" ]
then
   PATH=${XILINX_EDK}/bin/${PLATFORM}:${XILINX_EDK}/gnu/microblaze/${PLATFORM}/bin:${XILINX_EDK}/gnu/powerpc-eabi/${PLATFORM}/bin:${PATH}
else
   PATH=${XILINX_EDK}/bin/${PLATFORM}:${XILINX_EDK}/gnu/microblaze/${PLATFORM}/bin:${XILINX_EDK}/gnu/powerpc-eabi/${PLATFORM}/bin
fi
export PATH

if [ -n "$LD_LIBRARY_PATH" ]
then
   LD_LIBRARY_PATH=${XILINX_EDK}/bin/${PLATFORM}:${LD_LIBRARY_PATH}
else
   LD_LIBRARY_PATH=${XILINX_EDK}/bin/${PLATFORM}
fi
export LD_LIBRARY_PATH

myxilinxrc=${HOME}/.qt/xilinxrc

if [ -d "${SYSCONF}/xilinxrc" -a ! -f "$myxilinxrc" ]
then cp "${SYSCONF}/xilinxrc" "$myxilinxrc"
elif [ -f "/Xilinx/xilinxrc" -a ! -f "$myxilinxrc" ]
then cp "/Xilinx/xilinxrc" "$myxilinxrc"
fi

```

Thanks in advance.

---

### Post by Tomosaur on 2007-01-27
Try this script instead:
```

PLATFORM=lin
XILINX_EDK=/video/microblaze/EDK/
export XILINX_EDK

if [ -n "$PATH" ]
then
   PATH=$PATH:${XILINX_EDK}/bin/${PLATFORM}:${XILINX_EDK}/gnu/microblaze/${PLATFORM}/bin:${XILINX_EDK}/gnu/powerpc-eabi/${PLATFORM}/bin
else
   PATH=${XILINX_EDK}/bin/${PLATFORM}:${XILINX_EDK}/gnu/microblaze/${PLATFORM}/bin:${XILINX_EDK}/gnu/powerpc-eabi/${PLATFORM}/bin
fi
export $PATH

if [ -n "$LD_LIBRARY_PATH" ]
then
   LD_LIBRARY_PATH=$LD_LIBRARY_PATH:${XILINX_EDK}/bin/${PLATFORM}
else
   LD_LIBRARY_PATH=${XILINX_EDK}/bin/${PLATFORM}
fi
export $LD_LIBRARY_PATH

myxilinxrc=${HOME}/.qt/xilinxrc

if [ -d "${SYSCONF}/xilinxrc" -a ! -f "$myxilinxrc" ]
then cp "${SYSCONF}/xilinxrc" "$myxilinxrc"
elif [ -f "/Xilinx/xilinxrc" -a ! -f "$myxilinxrc" ]
then cp "/Xilinx/xilinxrc" "$myxilinxrc"
fi

```

---

### Post by phormion on 2007-01-27
jaymode, if you want the PATH variable to be modified in the current shell, you need to 'source' the script instead of executing it - executing the script will create a new subshell, set the PATH and LD_LIBRARY_PATH there, and then exit. With bash, you can source the script using either: 

```

$ source /path/to/script.sh

```

or, more concisely: 

```

$ . /path/to/script.sh

```

In that way you can test that the variables get set. It might work if the script is sourced from another script in order to set up the environment, otherwise, the settings will be lost.

---

