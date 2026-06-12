---
title: "Error: Unclassifiable statement at (1)"
date: 2011-11-05
forum: Programming Talk
---

### Post by dareymon on 2011-11-05
Hi Everyone!

I'm having this error while compiling the Prep_sources_chem which is used in the wrf model that i am using.

Attached is the code and this is the command im using.

ram@1111QUIEL:~/Prep_sources_chem_cptec_wrf/bin$ make
gfortran -c -ffree-form -O2 -fconvert=big-endian -I/usr/local/netcdf/include -L/usr/local/netcdf/lib -lnetcdf  ..//chem1_list.f90 ..//var_tables.f90 ..//grid_dims.f90 ..//io_params.f90 ..//vtab_fill.f90 ..//node_mod.f90 ..//mem_grid.f90 ..//rconstants.f90 ..//rams_grid.f90 ..//lllc_utils.f90 ..//adap_init_prepchem.f90 ..//gridset_prepchem.f90 ..//grid_dims_output.f90 ..//anheader.f90 ..//AeM_emission_factors.f90 ..//3bem_plumerise.f90 ..//emission_fields.f90 ..//cetesb_update.f90 ..//extrapolacao_update.f90 ..//retro_emissions.f90 ..//gfedv2_8days_emissions.f90 ..//edgar_emissions.f90 ..//gocart_emissions.f90 ..//gocart_background.f90 ..//fwb_awb_emissions.f90 ..//biogenic_emissions.f90 ..//fire_properties.f90 ..//3bem_emissions.f90 ..//convert_retro_to_racm.f90 ..//convert_AeM_to_racm.f90 ..//convert_bioge_to_racm.f90 ..//prep_chem_sources_utils.f90 ..//prep_chem_sources.f90
..//fwb_awb_emissions.f90:174:

area = cos(0.5*(latFWBAWB(j)+ &
1
Error: Unclassifiable statement at (1)
make: *** [prep_chem_sources.a] Error 1

I hope you can help me from this error,
Im using ubuntu 10.04
and the gfortran version i am using is

Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.4.3-4ubuntu5' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --program-suffix=-4.4 --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-plugin --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i486 --with-tune=generic --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5)

Thank you in advance

---

### Post by ofnuts on 2011-11-05
Googling you problem, it seem th error is related to wether you use the Fortran90 standard, that allows free formatting, or the older Fortran77 which requires fixed formating (actually code should start in column 7).

But you seem to be using fortran90 (-ffree-form and thje varoius .f90 extensions). But check that gfortran is really thinking the same and compiling for F90.

---

