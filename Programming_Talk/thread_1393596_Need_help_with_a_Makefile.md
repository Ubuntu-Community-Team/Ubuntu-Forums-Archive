---
title: "Need help with a Makefile"
date: 2010-01-29
forum: Programming Talk
---

### Post by whein on 2010-01-29
Is there a way to launch a process from within a makefile that executes in a separate (non-blocking) thread?  I.e. I would type "make foo" and then the makefile would do it's thing with the last step being to launch a program that I want to leave running in the background but have the makefile terminate and give me back the command prompt to enter the next command.  If it matters I'm using a makefile executing on WindowsXP.

My current makefile is:
```

VERILOGEX = .v # Verilog file extension

#iverilog CONFIG
VERILOG_CMD = iverilog
#VERILOG_FLAGS  =

# VVP (iverilog runtime engine)
VVP_CMD = vvp
#VVP_FLAGS =

#Simulation Vars
SIMDIR = .\simulation
DUMPTYPE = vcd
DUMPEXT = vcd
#DUMPTYPE = lxt2
#DUMPEXT = lxt

#Viewer
WAVEFORM_VIEWER = gtkwave # Waveform viewer executable

#SourceFiles
SOURCESLIST = .\sources.txt

all: compile run view

simulate: compile run

file_check:
ifeq ($(strip $(FILES)),)
		@echo "FILES not set. Use FILES=value to set it. Put mutltiple files in quotes"
		@exit 2
endif

testbench_check:
ifeq ($(strip $(TESTBENCH)),)
		@echo "TESTBENCH not set. Use TESTBENCH=value to set it."
		@exit 2
endif

check: file_check
	$(VERILOG_CMD) -t null $(FILES)

# Setup up project directory
new :
	echo "Setting up project ${PROJECT}"
	mkdir src testbench simulation


compile : testbench_check
	mkdir -p simulation
	$(VERILOG_CMD) -o  $(SIMDIR)\$(TESTBENCH) -s $(TESTBENCH) -c$(SOURCESLIST)

run : testbench_check
	$(VVP_CMD) $(SIMDIR)\$(TESTBENCH) -$(DUMPTYPE) $(VVP_FLAGS)
	mv dump.$(DUMPEXT) $(SIMDIR)\$(TESTBENCH).$(DUMPTYPE)

view : testbench_check
	$(WAVEFORM_VIEWER)  $(SIMDIR)\$(TESTBENCH).$(DUMPEXT)

clean : test_bench_check
	rm $(SIM_DIR)\$(TESTBENCH)*

```

---

