---
title: "Running a script with permissions."
date: 2011-12-04
forum: New to Ubuntu
---

### Post by HypnoFunk on 2011-12-04
Hello there, I have recently been given a script to run on my Unbuntu (Natty Narwhal) laptop, the script is below; 

```
#!/bin/bash
# versions of the various packages to install
fastjet=fastjet-2.4.3
hepmc=HepMC-2.06.05
lhapdf=lhapdf-5.8.5
rivet=tags/rivet-1.5.1
thepeg=branches/release-1-7
herwig=branches/release-2-5
location=`pwd`
install_gsl=false
gsl=gsl-1.15
# number of processes to run (~no of cores +1 or 2)
nproc=6
# get build and install gsl
if $install_gsl; then
    wget http://www.mirrorservice.org/sites/ftp.gnu.org/gnu/gsl/$gsl.tar.gz
    tar xzf $gsl.tar.gz
    cd $gsl
    ./configure --prefix=$location
    make -j $nproc
    make -j $nproc
    make install
    cd ..
    with_gsl=--with-gsl=$location
else
    with_gsl=
fi
# get, build and install fastjet
wget http://www.lpthe.jussieu.fr/~salam/fastjet/repo/$fastjet.tar.gz
tar xzf $fastjet.tar.gz
cd $fastjet
./configure --prefix=$location --enable-allplugins
make -j$nproc 
make install
cd ..
# get, build and install hepmc
wget http://lcgapp.cern.ch/project/simu/HepMC/download/$hepmc.tar.gz
tar xzf $hepmc.tar.gz
cd $hepmc
./configure --prefix=$location --with-momentum=GEV --with-length=MM
make -j $nproc install
cd ..
# get, build and install lhapdf
wget http://www.hepforge.org/archive/lhapdf/$lhapdf.tar.gz
tar xzf $lhapdf.tar.gz
cd $lhapdf
./configure --prefix=$location -enable-pdfsets=all
make -j $nproc install
cd ..
# get and build rivet
svn co http://svn.hepforge.org/rivet/$rivet rivet
cd rivet
autoreconf -vi
./configure --prefix=$location $with_gsl --with-hepmc=$location --with-fastjet=$location
make -j $nproc install
cd ..
# get and build ThePEG
svn co http://svn.hepforge.org/thepeg/$thepeg/ThePEG ThePEG
cd ThePEG
autoreconf -vi
./configure --prefix=$location $with_gsl --with-LHAPDF=$location/lib --enable-unitchecks \
            --with-rivet=$location --with-hepmc=$location
make -j $nproc install
cd ..
# get and build Herwig++
svn co http://svn.hepforge.org/herwig/$herwig Herwig++
cd Herwig++
autoreconf -vi
./configure --with-fastjet=$location $with_gsl --with-thepeg=$location \
            --with-thepeg-headers=$location --prefix=$location --enable-debug
make -j $nproc install
cd ..
```

The file name is "bootstrap.script". Does anyone know how I might run this script? And the terminal command I would need to type in. Would I need to be in particular directory to do this, or just the directory that the script is in? 

In addition, would I need to set any permissions?

Thank you to anyone that can help.

---

### Post by Lars Noodén on 2011-12-04
```

# set executable bit
chmod +x bootstrap.script

# run script
./bootstrap.script

```

---

### Post by dcsoldschool53 on 2011-12-05
> **HypnoFunk said:**
> Hello there, I have recently been given a script to run on my Unbuntu (Natty Narwhal) laptop, the script is below; 

```
#!/bin/bash
# versions of the various packages to install
fastjet=fastjet-2.4.3
hepmc=HepMC-2.06.05
lhapdf=lhapdf-5.8.5
rivet=tags/rivet-1.5.1
thepeg=branches/release-1-7
herwig=branches/release-2-5
location=`pwd`
install_gsl=false
gsl=gsl-1.15
# number of processes to run (~no of cores +1 or 2)
nproc=6
# get build and install gsl
if $install_gsl; then
    wget http://www.mirrorservice.org/sites/ftp.gnu.org/gnu/gsl/$gsl.tar.gz
    tar xzf $gsl.tar.gz
    cd $gsl
    ./configure --prefix=$location
    make -j $nproc
    make -j $nproc
    make install
    cd ..
    with_gsl=--with-gsl=$location
else
    with_gsl=
fi
# get, build and install fastjet
wget http://www.lpthe.jussieu.fr/~salam/fastjet/repo/$fastjet.tar.gz
tar xzf $fastjet.tar.gz
cd $fastjet
./configure --prefix=$location --enable-allplugins
make -j$nproc 
make install
cd ..
# get, build and install hepmc
wget http://lcgapp.cern.ch/project/simu/HepMC/download/$hepmc.tar.gz
tar xzf $hepmc.tar.gz
cd $hepmc
./configure --prefix=$location --with-momentum=GEV --with-length=MM
make -j $nproc install
cd ..
# get, build and install lhapdf
wget http://www.hepforge.org/archive/lhapdf/$lhapdf.tar.gz
tar xzf $lhapdf.tar.gz
cd $lhapdf
./configure --prefix=$location -enable-pdfsets=all
make -j $nproc install
cd ..
# get and build rivet
svn co http://svn.hepforge.org/rivet/$rivet rivet
cd rivet
autoreconf -vi
./configure --prefix=$location $with_gsl --with-hepmc=$location --with-fastjet=$location
make -j $nproc install
cd ..
# get and build ThePEG
svn co http://svn.hepforge.org/thepeg/$thepeg/ThePEG ThePEG
cd ThePEG
autoreconf -vi
./configure --prefix=$location $with_gsl --with-LHAPDF=$location/lib --enable-unitchecks \
            --with-rivet=$location --with-hepmc=$location
make -j $nproc install
cd ..
# get and build Herwig++
svn co http://svn.hepforge.org/herwig/$herwig Herwig++
cd Herwig++
autoreconf -vi
./configure --with-fastjet=$location $with_gsl --with-thepeg=$location \
            --with-thepeg-headers=$location --prefix=$location --enable-debug
make -j $nproc install
cd ..
```The file name is "bootstrap.script". Does anyone know how I might run this script? And the terminal command I would need to type in. Would I need to be in particular directory to do this, or just the directory that the script is in? 

In addition, would I need to set any permissions?

Thank you to anyone that can help.

Yes, you must be in the directory where you have stored the script to run it. Goto that directory in a terminal, and do as Lars said.

I hope this will help you.

---

