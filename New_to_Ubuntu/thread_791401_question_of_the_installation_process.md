---
title: "question of the installation process"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Adrastos on 2008-05-12
I am trying to install a molecular simulation software named dl_poly.In the installation there is a choice which is not very clear.
The installation instructions are as follows:-

[B]The compilation of the program is initiated by typing the command
make target
where target is the specification of the required machine (eg hpcx). 

To determine which targets are already defined in the makefile, typing the command make To determine which targets are already defined in the makefile, typing the command make
without a nominated target will produce a list of known targets. without a nominated target will produce a list of known targets.[/B]

When i gave the command make then i got a message which is as follows:
[I]Permissible targets for this Makefile are

nag-f95 (serial) 
gfortran (serial) 
cray-t3e (serial) 
macosx (serial) 
intel-linux-ifc (serial) 
dec-alpha (serial) 
dec-alpga-ev6 (serial) 
alpha-linux (serial) 
exemplar (serial) 
hp-c240 (serial) 
aix (serial) 
rs6k (serial) 
rs6k-pwr3 (serial) 
pentium-absoft (serial) 
pentium-portland (serial) 
sg10k (serial) 
sg2k (serial) 
sg2k-r5k (serial)
sun-ultra (serial) 
Please examine Makefile for details
[/I]
Now the make file is as follows:-

[I]# Master makefile for DL_POLY_2.0 
# Author: W. Smith September 2007
# 
#=======================================================================
# Define default settings
#=======================================================================

BINROOT = ../execute
CC  = gcc
EX = DLPOLY.X
EXE = $(BINROOT)/$(EX)
FC=undefined
SHELL=/bin/sh
TYPE=seq

#=====================================================================
# Define object files

OBJ_MOD = parse_module.o setup_module.o error_module.o \
	site_module.o config_module.o pair_module.o utility_module.o \
	tether_module.o vdw_module.o property_module.o rigid_body_module.o \
	angles_module.o bonds_module.o shake_module.o \
	inversion_module.o dihedral_module.o core_shell_module.o \
	exclude_module.o ewald_module.o coulomb_module.o\
	external_field_module.o four_body_module.o hkewald_module.o \
	metal_module.o ensemble_tools_module.o temp_scalers_module.o \
	three_body_module.o spme_module.o \
	tersoff_module.o neu_coul_module.o \
	nlist_builders_module.o forces_module.o \
	lf_motion_module.o lf_rotation1_module.o lf_rotation2_module.o \
	vv_motion_module.o vv_rotation1_module.o vv_rotation2_module.o \
	pmf_module.o  integrator_module.o define_system_module.o \
	optimiser_module.o hyper_dynamics_module.o driver_module.o

OBJ_SRC = dlpoly.o

OBJ_PAR = serial.o

#=====================================================================
# Define targets
all:
	@echo "Error - please specify a target machine!"
	@echo "Permissible targets for this Makefile are:"
	@echo "                                          "
	@echo "nag-f95                    (serial)"
	@echo "gfortran                   (serial)"
	@echo "cray-t3e                   (serial)"
	@echo "macosx                     (serial)"
	@echo "intel-linux-ifc            (serial)"
	@echo "dec-alpha                  (serial)"
	@echo "dec-alpga-ev6              (serial)"
	@echo "alpha-linux                (serial)"
	@echo "exemplar                   (serial)"
	@echo "hp-c240                    (serial)"
	@echo "aix                        (serial)"
	@echo "rs6k                       (serial)"
	@echo "rs6k-pwr3                  (serial)"
	@echo "pentium-absoft             (serial)"
	@echo "pentium-portland           (serial)"
	@echo "sg10k                      (serial)"
	@echo "sg2k                       (serial)"
	@echo "sg2k-r5k                   (serial)"
	@echo "sun-ultra                  (serial)"
	@echo "         "
	@echo "Please examine Makefile for details"

# system specific targets follow :

#========================== NAG Fortran 95 ===========================
nag-f95:
	$(MAKE) LD="f95 -o" LDFLAGS="" \
	FC=f95 FFLAGS="-c -O -fixed -kind=byte" \
	EX=$(EX) BINROOT=$(BINROOT) $(TYPE)

#========== GNU Fortran =================================================
gfortran:
	$(MAKE) LD="gfortran -o" LDFLAGS="" FC=gfortran \
	FFLAGS="-c -O2 -ffast-math" \
	EX=$(EX) BINROOT=$(BINROOT) $(TYPE)

#========== Cray t3e (serial) ===========================================
cray-t3e:
	$(MAKE) LD="f90 -o" LDFLAGS="" FC=f90 \
	FFLAGS="-c -dp -O3,aggress,unroll2,nojump" \
	EX=$(EX) BINROOT=$(BINROOT) $(TYPE)

#============= MacOSX (Darwin) version: derived from AIX ===============
macosx: 
	$(MAKE) FC=xlf FFLAGS="-c -O3 -qstrict -qipa -qarch=g5 -qnosave" \
	intlist.o
	$(MAKE) LD="xlf -o" LDFLAGS="" FC=xlf FFLAGS="-c -O3 -qstrict -qarch=g5 -qnosave"\
	EX=$(EX) BINROOT=$(BINROOT) $(TYPE)

#========== Intel Linux IFC =============================================
intel-linux-ifc: 
	$(MAKE) FC=ifc LD="ifc -o" FFLAGS="-c -O3 -w95 -w" \
	LDFLAGS="-Vaxlib -static" \
	EX=$(EX) BINROOT=$(BINROOT) $(TYPE)

#========== DEC Alpha ===================================================
dec-alpha:  
	$(MAKE) LD="f90 -o" FC=f90 FFLAGS="-c -fast" \
	LDFLAGS="-math_library fast -assume noaccuracy_sensitive" \
	EX=$(EX) BINROOT=$(BINROOT) $(TYPE)

#========== DEC Alpha ev6 ===============================================
dec-alpha-ev6:  
	$(MAKE) LD="f90 -o" FC=f90 FFLAGS="-c -arch ev6 -fast" \
	LDFLAGS="-arch ev6 -math_library fast -assume noaccuracy_sensitive"  \
	EX=$(EX) BINROOT=$(BINROOT) $(TYPE)

#======== Alpha Linux ===================================================
alpha-linux: 
	$(MAKE) FC=fort LD="fort -o" FFLAGS="-c -O -fast" \
	LDFLAGS="" EX=$(EX) BINROOT=$(BINROOT) $(TYPE)

#========= Convex/HP exemplar (serial) =================================
exemplar:  
	$(MAKE) LD="f90 -o" LDFLAGS=""  \
	FC=f90 FFLAGS=" -c +ppu +O2 +DA2.0" \
	 EX=$(EX) BINROOT=$(BINROOT) $(TYPE)

#========= HP PA 9000 / C240 (serial) ==================================
hp-c240:  
	$(MAKE) LD="f90 -o" LDFLAGS=  FC=f90 FFLAGS=" -c +ppu +O2 +DA2.0" \
	EX=$(EX) BINROOT=$(BINROOT) $(TYPE)

#============= IBM (AIX) Workstation version =============================
aix: 
	$(MAKE) FC=mpxlf FFLAGS="-c -NS2048 -qarch=pwr2 -qnosave" \
	intlist.o 
	$(MAKE) LD="xlf -o" LDFLAGS="" FC=xlf FFLAGS="-c -O3 -NS2048 -qarch=pwr2 -qnosave"\
	EX=$(EX) BINROOT=$(BINROOT) $(TYPE)

#========= RS/6000 P2SC (serial) =========================================
rs6k:  
	$(MAKE) LD="xlf -o" LDFLAGS=  FC=xlf \
	FFLAGS="-c -O -qarch=pwr2 -qtune=pwr2" TIMER="" \
	EX=$(EX) BINROOT=$(BINROOT) $(TYPE)

#========= RS/6000 Power3 (serial) =======================================
rs6k-pwr3:  
	$(MAKE) LD="xlf -o" LDFLAGS="-L/usr/local/lib -lmass -lessl"  \
	FC=xlf FFLAGS="-c -O -qnosave -qarch=pwr3" \
	EX=$(EX) BINROOT=$(BINROOT) $(TYPE)

#========== PentiumII (absoft) (serial) ==================================
pentium-absoft: 
	$(MAKE) LD="/usr/bin/f90 -o" LDFLAGS="-lfio" \
	FC=/usr/bin/f90 FFLAGS="-c -YEXT_NAMES=LCS -B108 -B100 -O" \
	EX=$(EX) BINROOT=$(BINROOT) $(TYPE)
 
#========== PentiumII (portland) (serial) ================================
pentium-portland: 
	$(MAKE) LD="/usr/local/pgi/linux86/bin/pgf90 -o" LDFLAGS="" \
	FC=/usr/local/pgi/linux86/bin/pgf90 FFLAGS="-c -O -Mdalign" \
	EX=$(EX) BINROOT=$(BINROOT) $(TYPE)

#======== Silicon Graphics 10000 Worskstation ============================
sg10k: 
	$(MAKE) LD="f90 -o" LDFLAGS="-lscs" \
	FC=f90 FFLAGS="-c -O2 -OPT:Olimit=0 -lscs" \
	EX=$(EX) BINROOT=$(BINROOT) $(TYPE)

#========= Silicon Graphics Origin 2000 (serial) =====================
sg2k:  
	$(MAKE) LD="f90 -o" LDFLAGS="-n32 -mips4"  FC=f90 \
	FFLAGS="-c -O3 -G 0 -mips4 -r10000 -c -r8 -n32" \
	EX=$(EX) BINROOT=$(BINROOT) $(TYPE)

#=== Silicon Graphics Origin 2000 (serial, Irix 6.5) =================
sg2k-i6.5:  
	$(MAKE) LD="f90 -o" LDFLAGS="-n32 -mips4 -IPA"  \
	FC=f90 FFLAGS="-c -n32 -mips4 -Ofast=ip27 -LNO:fusion=2" \
	EX=$(EX) BINROOT=$(BINROOT) $(TYPE)

#=== Silicon Graphics O2 R5k (serial) ================================
sg2-r5k:  
	$(MAKE) LD="f90 -o" LDFLAGS="-n32 -mips4"  \
	FC=f90 FFLAGS="-c -O3 -G 0 -mips4 -r5000 -c -r8 -n32" \
	EX=$(EX) BINROOT=$(BINROOT) $(TYPE)

#======== Sun Ultra-2 (serial) =======================================
sun-ultra:  
	$(MAKE) LD="/opt/SUNWspro/bin/f90 -o" LDFLAGS=  \
	FC=/opt/SUNWspro/bin/f90 \
	FFLAGS="-c -fnonstd -xarch=v8plusa -xchip=ultra -O2 -libmil -dalign" \
	EX=$(EX) BINROOT=$(BINROOT) $(TYPE)

#=====================================================================
# Default code for sequential execution

seq: check $(OBJ_MOD) $(OBJ_PAR) $(OBJ_SRC)
	$(LD) $(EX) $(LDFLAGS) $(OBJ_MOD) $(OBJ_PAR) $(OBJ_SRC)
	mv $(EX) $(EXE)

#=====================================================================
# Check that a machine has been specified
check:
	@if test $(FC) = "undefined";\
	then echo "You must specify a target machine!"; \
	exit 99;\
	fi

#=====================================================================
# Clean up the source directory
clean:
	rm -f $(OBJ_MOD) $(OBJ_PAR) $(OBJ_SRC) *.mod

#=====================================================================
# Declare dependencies
.f.o: 
	$(FC) $(FFLAGS) $*.f
.c.o: 
	$(CC) -c $*.c

#=====================================================================
# Declare dependency on module files

$(OBJ_SRC): $(OBJ_MOD)[/I]

I am using Ubuntu 8.04 
and my PC configuration is :-
Intel Core 2 Duo 1.86 GHz
Intel 965 motherboard

Please help in choosing the target machine type.

---

### Post by cwgatling on 2008-05-12
I would try using 'make intel-linux-ifc' as you have an Intel processor and you're running Linux. It will require a fortran compiler.

---

### Post by mister_pink on 2008-05-12
I think you'll want gfortran. Its the GNU fortran compiler. The intel-ifc is the Intel Fortran Compiler that I don't suppose you'll have. You'll need gfortran installed:
```
sudo apt-get install gfortran
```

---

### Post by Adrastos on 2008-05-13
@cwgatling: I had also tried that but it gave errors.Then i tried each and every option but still got errors.

@mister_pink: Yes you are right.After posting the problem here i tried for sometime and found that after installing the gfortran and after that compiling the code by giving the target machine as gfortran it worked.

Thanks a lot to both of you for reply.

---

