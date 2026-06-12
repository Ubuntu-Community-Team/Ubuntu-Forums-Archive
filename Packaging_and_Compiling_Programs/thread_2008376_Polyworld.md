---
title: "Polyworld"
date: 2012-06-22
forum: Packaging and Compiling Programs
---

### Post by jarro221 on 2012-06-22
Hi. 
I need some help building [polyworld]("http://www.beanblossom.in.us/larryy/polyworld.html").
[*Ubuntu* *12.04*]
I followed the instructions from: [http://www.beanblossom.in.us/larryy/BuildingPolyworld.html](http://www.beanblossom.in.us/larryy/BuildingPolyworld.html)

when i run "make" i get:

```
ppp@pppoe:~$ cd polyworld/
ppp@pppoe:~/polyworld$ make
scons -f scripts/build/SConstruct
scons: Reading SConscript files ...
Failed locating library GL
make: *** [all] Error 1

```so i started looking around the polyworld/scripts/build/ folder trying to find what exactly scons is complaining about
and i found "scons_util.py" looking for "gl.h" in "/usr/include/GL"

> ```
def import_OpenGL(env):
    env.Append( CPPPATH = [which('gl.h',
                                 dir = True,
                                 path = ['/usr/include/GL',
                                         '/System/Library/Frameworks/OpenGL.framework/Versions/A/Headers',
                                         '/System/Library/Frameworks/AGL.framework/Versions/A/Headers/'],
                                 err = 'Cannot locate OpenGL')] )

    if PFM == 'linux':
        addlib(env, 'GL')
        addlib(env, 'GLU')
    elif PFM == 'mac':
        addlib(env, 'AGL')
        addlib(env, 'OpenGL')
```and the path is correct, file is there

```
ppp@pppoe:/usr/include/GL$ ls
freeglut_ext.h  freeglut_std.h  glext.h  gl_mangle.h  glu_mangle.h  glxew.h   glx.h     glx_mangle.h  glxproto.h   internal
freeglut.h      glew.h          gl.h     glu.h        glut.h        glxext.h  glxint.h  glxmd.h       glxtokens.h  wglew.h
```So what can i do to get polyworld to build ?

Please help.

---

### Post by NNOTM on 2012-06-28
I had a similar problem, but with the python library. I had python installed, and the folder was there, but it couldn't locate the library. But I've found **[this]("http://www.reddit.com/comments/aadve/using_evolution_to_design_ai")** on reddit where someone has the same problem with gsl - and he had to install the dev version of the library.

I installed the library python-dev and it worked. So I guess you'll probably have to install libgl-dev or something like that, I don't know if that's really the name of it.

---

### Post by oldos2er on 2012-06-28
Moved to Packaging and Compiling Programs.

---

### Post by jarro221 on 2012-07-04
Hi.
So i'm still trying to build this thing, no luck so far.

As for the dev packages, i think i have all the required ones.

gl.h is provided by "mesa-common-dev" package and i have it installed
(version  8.0.2-0ubuntu3.1)

I'm starting to think something is wrong with the scripts Scons is using to set up the build
and since i don't know much about Scons or Python for that matter, can someone have a look at these scripts and check if there's no errors?

Makefile:

```
# This file should never be executable

SCONS = scons -f scripts/build/SConstruct

.PHONY: all clean \
    app Polyworld \
    comp CalcComplexity \
    mp PwMoviePlayer \
    rancheck \
    proputil \
    qt_clust

all:
    ${SCONS}

clean:
    ${SCONS} --clean
    rm -rf .bld
    rm -rf bin
    rm -rf src # this just has symbolic links
    rm -f .sconsign.dblite
    rm -f config.log

app Polyworld:
    ${SCONS} Polyworld

comp CalcComplexity:
    ${SCONS} bin/CalcComplexity

mp PwMoviePlayer:
    ${SCONS} bin/PwMoviePlayer

rancheck:
    ${SCONS} bin/rancheck

proputil:
    ${SCONS} bin/proputil

qt_clust:
    ${SCONS} bin/qt_clust
```scripts/build/SConstruct:

```
PERFORMANCE_PROFILER = False # temp hack. add command-line switch

import os
import sys

from scons_util import exclude, find, init_env, relocate_paths, export_dynamic
from scons_util import import_OpenGL, import_OpenMP, import_GSL, import_Qt, import_zlib, import_python

SRCDIRS = ['src/' + x
           for x in ['agent',
                     'app',
                     'brain',
                     'complexity',
                     'debugger',
                     'environment',
                     'genome',
                     'graphics',
                     'logs',
                     'proplib',
                     'main',
                     'monitor',
                     'tools',
                     'ui',
                     'utils']]

def build():
    envs = env_create()

    Default( build_Polyworld(envs['Polyworld']) )
    Default( build_CalcComplexity(envs['CalcComplexity']) )
    Default( build_PwMoviePlayer(envs['PwMoviePlayer']) )
    Default( build_rancheck(envs['rancheck']) )
    Default( build_proputil(envs['proputil']) )
    Default( build_pmvutil(envs['pmvutil']) )
    Default( build_qt_clust(envs['qt_clust']) )
    build_cppprops(envs['cppprops'])

def build_Polyworld(env):
    blddir = '.bld/Polyworld'

    srcdirs = exclude(SRCDIRS, ['src/tools'])
    env.Replace( CPPPATH = exclude(env['CPPPATH'], ['src/tools']) )

    sources = Flatten([find(srcdir,
                            name = '*.cp')
                       for srcdir in srcdirs])

    env.VariantDir(blddir, 'src', False)

    return env.Program('Polyworld',
                       relocate_paths(sources,
                                      'src',
                                      blddir))

def build_CalcComplexity(env):
    blddir = '.bld/CalcComplexity'

    sources = find('src/tools/CalcComplexity',
                   name = '*.cpp')
    sources += find('src/complexity',
                    name = 'complexity_*.cp')
    sources += ['src/utils/datalib.cp',
                'src/utils/Variant.cp',
                'src/utils/AbstractFile.cp',
                'src/utils/misc.cp']

    env.VariantDir(blddir, 'src', False)

    return env.Program('bin/CalcComplexity',
                       relocate_paths(sources,
                                      'src',
                                      blddir))

def build_PwMoviePlayer(env):
    blddir = '.bld/PwMoviePlayer'

    sources = find('src/tools/PwMoviePlayer',
                   name = '*.cp')
    sources += ['src/utils/PwMovieUtils.cp']

    env.VariantDir(blddir, 'src', False)

    return env.Program('bin/PwMoviePlayer',
                       relocate_paths(sources,
                                      'src',
                                      blddir))

def build_rancheck(env):
    blddir = '.bld/rancheck'

    sources = ['src/tools/rancheck/rancheck.c']

    env.VariantDir(blddir, 'src', False)

    return env.Program('bin/rancheck',
                       relocate_paths(sources,
                                      'src',
                                      blddir))

def build_proputil(env):
    blddir = '.bld/proputil'

    sources = find('src/tools/proputil',
                   name = '*.cp')
    sources += find( 'src/proplib',
                     name = '*.cp',
                     ignore = ['state.cp'] )
    sources += ['src/utils/misc.cp']

    env.VariantDir(blddir, 'src', False)

    return env.Program('bin/proputil',
                       relocate_paths(sources,
                                      'src',
                                      blddir))

def build_pmvutil(env):
    blddir = '.bld/pmvutil'

    sources = find('src/tools/pmvutil',
                   name = '*.cp')
    sources += ['src/utils/PwMovieUtils.cp']

    env.VariantDir(blddir, 'src', False)

    return env.Program('bin/pmvutil',
                       relocate_paths(sources,
                                      'src',
                                      blddir))

def build_qt_clust(env):
    blddir = '.bld/qt_clust'

    sources = ['src/tools/clustering/qt_clust.cpp']

    env.VariantDir(blddir, 'src', False)

    return env.Program('bin/qt_clust',
                       relocate_paths(sources,
                                      'src',
                                      blddir))

def build_cppprops(env):
    blddir = '.bld/cppprops/bld'

    sources = ['.bld/cppprops/src/generated.cpp']

    env.VariantDir(blddir, '.bld/cppprops/src', False)

    return env.SharedLibrary( '.bld/cppprops/bin/cppprops',
                              sources )

def env_create():
    envs = {}


    env = env_common = init_env(Environment())
    env.Append( CPPSUFFIXES = ['.cp'] )
    #cpp_flags = ['-g', '-Wall', '-O2' ]
    cpp_flags = ['-g', '-Wall', '-Wno-format-security', '-std=gnu++0x' ]

    if PERFORMANCE_PROFILER:
        # use the gnu gprof
        cpp_flags += ['-pg']
        env.Append( LINKFLAGS = ['-pg'] )

    try:
        cpp_flags += os.environ['CPPFLAGS'].split(' ')
    except KeyError:
        pass
    env.Append( CPPFLAGS = cpp_flags )      
    env.Append( CPPPATH = find('src',
                               type = 'dir') )
    try:
        env.Append( LINKFLAGS = os.environ['LDFLAGS'].split(' ') )
    except KeyError:
        pass

    # This allows proplib dynamic properties to reference globals in Polyworld.
    export_dynamic(env)

    import_OpenMP(env)
    import_GSL(env)

    env = envs['Polyworld'] = env_common.Clone()    
    import_OpenGL(env)
    import_Qt(env,
              qtversion = 4,
              qtmodules = ['QtCore',
                           'QtGui',
                           'QtOpenGL'])
    import_zlib(env)
    try:
        python_version = os.environ['PYTHONVER']
    except KeyError:
        python_version = None
    
    if python_version:
        import_python(env, python_version)
    else:
        import_python(env)

    env = envs['CalcComplexity'] = env_common.Clone()
    import_zlib(env)

    envs['PwMoviePlayer'] = envs['Polyworld'].Clone()

    envs['rancheck'] = envs['CalcComplexity'].Clone()

    envs['proputil'] = envs['CalcComplexity'].Clone()

    if python_version:
        import_python( envs['proputil'], python_version )
    else:
        import_python( envs['proputil'] )

    envs['pmvutil'] = envs['PwMoviePlayer'].Clone()

    envs['qt_clust'] = envs['CalcComplexity'].Clone()

    envs['cppprops'] = envs['Polyworld'].Clone()

    return envs

def hack_addCpExtension():
    # treat *.cp as C++ source
    module = __import__('SCons.Tool.c++',
                        globals(),
                        locals(),
                        ['CXXSuffixes'])
    module.CXXSuffixes += ['.cp']

    # scan *.cp for #include
    from SCons.Scanner.C import CScanner
    builder_object = DefaultEnvironment()["BUILDERS"]["Object"]
    builder_object.source_scanner.add_scanner('.cp',
                                              CScanner())

def hack_createSrcDir():
    if not os.path.exists('src'):
        os.mkdir('src')

    for dir in SRCDIRS:
        if not os.path.exists(dir):
            src = '../' + dir[4:] # strip src/
            dst = dir
            os.symlink(src,dst)

################################################################################

hack_addCpExtension()
hack_createSrcDir()

build()
```scripts/build/scons_util.py:

```
import os
import re
import sys


################################################################################
###
### FUNCTION init_env
###
################################################################################
def init_env(env):
    env.Append( LIBPATH = ['/usr/local/lib',
                           '/usr/lib'] )

    if PFM == 'linux':
        env.Append( DEFAULTFRAMEWORKPATH = [] )
        env.Append( FRAMEWORKPATH = [] )
        env.Append( LIBPATH = ['/usr/lib/x86_64-linux-gnu'] )
    elif PFM == 'mac':
        env.Append( DEFAULTFRAMEWORKPATH = ['/System/Library/Frameworks',
                                            '/Library/Frameworks'] )
        env.Append( FRAMEWORKPATH = [] )
        
    return env

################################################################################
###
### FUNCTION import_OpenGL
###
################################################################################
def import_OpenGL(env):
    env.Append( CPPPATH = [which('gl.h',
                                 dir = True,
                                 path = ['/usr/include/GL',
                                         '/System/Library/Frameworks/OpenGL.framework/Versions/A/Headers',
                                         '/System/Library/Frameworks/AGL.framework/Versions/A/Headers/'],
                                 err = 'Cannot locate OpenGL')] )

    if PFM == 'linux':
        addlib(env, 'GL')
        addlib(env, 'GLU')
    elif PFM == 'mac':
        addlib(env, 'AGL')
        addlib(env, 'OpenGL')

################################################################################
###
### FUNCTION import_OpenMP
###
################################################################################
def import_OpenMP(env):
    env.Append( LIBS = 'gomp' )
    env.Append( CPPFLAGS = '-fopenmp' )

################################################################################
###
### FUNCTION import_GSL
###
################################################################################
def import_GSL(env):
    addlib(env, 'gsl')
    addlib(env, 'gslcblas')

################################################################################
###
### FUNCTION import_zlib
###
################################################################################
def import_zlib(env):
    addlib(env, 'z')

################################################################################
###
### FUNCTION import_python
###
################################################################################
def import_python(env, version=None):
    if PFM == 'linux':
        if not version: version='2.7'
        env.Append( CPPPATH = ['/usr/include/python'+version] )
    elif PFM == 'mac':
        if not version: version='2.6'
        env.Append( CPPPATH = ['/System/Library/Frameworks/Python.framework/Versions/'+version+'/include/python'+version] )
    else:
        assert(False)

    addlib(env, 'python'+version)

################################################################################
###
### FUNCTION import_Qt
###
################################################################################
def import_Qt(env,
              qtversion = 4,
              qtmodules = ['QtCore']):

    def expand(path, module = ""):
        return map(lambda p: p.replace('$MODULE', module).replace('$VERSION',str(qtversion)),
                   path)

    ###
    ### Include Path
    ###
    if PFM == 'linux':
        qthome = None
        PFM_CPPPATH = ['/usr/share/qt$VERSION/include/$MODULE']

        env.Append( CPPPATH = expand(['/usr/share/qt$VERSION/include/']) )
    elif PFM == 'mac':
        qthome = os.path.expanduser( '~/QtSDK/Desktop/Qt/4.8.1/gcc' )
        if os.path.exists( qthome ):
            PFM_CPPPATH = [qthome + '/include/$MODULE']
        else:
            qthome = None
            PFM_CPPPATH = ['/Library/Frameworks/$MODULE.framework/Versions/$VERSION/Headers']
    else:
        assert(false)

    for mod in qtmodules:
        env.AppendUnique( CPPPATH = [which(mod,
                                           dir = True,
                                           path = expand(PFM_CPPPATH, mod),
                                           err = 'Cannot locate ' + mod)] )

    ###
    ### Libraries
    ###
    if PFM == 'linux':
        env.Append( LIBPATH = expand(['/usr/share/qt$VERSION/lib']) )

    for mod in qtmodules:
        if qthome:
            addlib( env, mod, path = [qthome + '/lib'] )
        else:
            addlib( env, mod )

    env.Replace( QT_LIB = None )

    ###
    ### Executables Path
    ###
    if qthome:
        env.Replace( QT_BINPATH = [qthome + '/bin'] )
    else:
        env.Replace( QT_BINPATH = [which('moc',
                                         dir = True,
                                         err = "Cannot locate Qt executables")] )

    ###
    ### Misc
    ###
    env.Replace( QTDIR = '/usr' ) # dummy. not needed since we explictly configure.
    env.Tool('qt')

    return env

################################################################################
###
### FUNCTION export_dynamic
###
################################################################################
def export_dynamic( env ):
    if PFM == 'linux':
        env.Append( LINKFLAGS = ['-rdynamic'] ) 
    elif PFM == 'mac':
        env.Append( LINKFLAGS = ['-undefined', 'dynamic_lookup'] )
    else:
        assert( False )

################################################################################
###
### FUNCTION find
###
################################################################################
def find(topdir = '.',
         type = None,
         name = None,
         regex = None,
         ignore = ['CVS'] ):

    assert((name == None and regex == None)
           or (name != None) ^ (regex != None))
    if type:
        assert(type in ['file', 'dir'])

    result = []

    if(name):
        # convert glob syntax to regex
        pattern = name.replace('.','\\.').replace('*','.*') + '$'
    elif(regex == None):
        pattern = '.*'
    else:
        pattern = regex

    cregex = re.compile(pattern)

    for dirinfo in os.walk(topdir):
        dirname = dirinfo[0]
        if type == None:
            children = dirinfo[1] + dirinfo[2]
        elif type == 'dir':
            children = dirinfo[1]
        elif type == 'file':
            children = dirinfo[2]
        else:
            assert(false)
        
        for filename in children:
            if filename in ignore:
                continue

            path = os.path.join(dirname, filename)

            if cregex.match(filename):
               result.append(path)

            if os.path.isdir(path) and os.path.islink(path):
                result += find(path,
                               type,
                               name,
                               regex)

    return result

################################################################################
###
### FUNCTION which
###
################################################################################
def which(name,
          dir = False,
          path = os.environ['PATH'].split(':'),
          err = None):

    for dir in path:
        p = os.path.join(dir, name)
        if os.path.exists(p):
            abspath = os.path.abspath(p)
            if dir:
                return os.path.dirname(abspath)
            else:
                return abspath
    if err:
        print err
        sys.exit(1)
    else:
        return None

################################################################################
###
### FUNCTION exclude
###
################################################################################
def exclude(dirs, exclude):
    def test(dir):
        for x in exclude:
            if dir.startswith(x):
                return False
        return True

    return filter(test, dirs)

################################################################################
###
### FUNCTION relocate_paths
###
################################################################################
def relocate_paths(sources, oldtop, newtop):
    n = len(str(oldtop))

    return map(lambda path: str(newtop) + '/' + path[n:],
               sources)

################################################################################
###
### FUNCTION libsuffixes
###
################################################################################
def libsuffixes():
    if PFM == 'linux':
        return ['.so', '.a']
    elif PFM == 'mac':
        return ['.dylib', '.so', '.a']
    else:
        assert(false)

################################################################################
###
### FUNCTION libprefix
###
################################################################################
def libprefix():
    if PFM == 'linux' or PFM == 'mac':
        return 'lib'
    else:
        assert(false)

################################################################################
###
### FUNCTION addlib
###
################################################################################
def addlib(env, libname, path = None):
    if not path:
        path = env['LIBPATH'] + env['FRAMEWORKPATH'] + env['DEFAULTFRAMEWORKPATH']

    for dir in path:
        if os.path.exists( os.path.join(dir, libname + '.framework') ):
                env.Append( FRAMEWORKS = [libname] )
                if dir not in env['DEFAULTFRAMEWORKPATH']:
                    env.AppendUnique( FRAMEWORKPATH = [dir] )
                return
        else:
            for libsuffix in libsuffixes():
                lib = libprefix() + libname + libsuffix

                if os.path.exists( os.path.join(dir, lib) ):
                    env.Append( LIBS = [libname] )
                    env.AppendUnique( LIBPATH = [dir])
                    return

    print 'Failed locating library', libname
    sys.exit(1)

################################################################################
###
### FUNCTION uname
###
################################################################################
def uname():
    type = os.popen('uname').readlines()[0].strip()

    if type.startswith('Darwin'):
        return 'mac'
    elif type.startswith('Linux'):
        return 'linux'
    else:
        assert(false)

PFM = uname()
```Edit:
If it helps here's a list of dev packages i have installed:

```
ppp@pppoe:~$ sudo dpkg-query -Wf '${Package}\n' |grep \.-dev
autotools-dev
dpkg-dev
freeglut3-dev
libalut-dev
libasound2-dev
libatk1.0-dev
libatkmm-1.6-dev
libavahi-client-dev
libavahi-common-dev
libavcodec-dev
libavformat-dev
libavutil-dev
libboost-date-time-dev
libboost-date-time1.46-dev
libboost-dev
libboost-serialization1.46-dev
libboost-thread-dev
libboost-thread1.46-dev
libboost1.46-dev
libc-dev-bin
libc6-dev
libcaca-dev
libcairo2-dev
libcairomm-1.0-dev
libcegui-mk2-dev
libdbus-1-dev
libdevil-dev
libdmx-dev
libdrm-dev
libexpat1-dev
libflac-dev
libfontconfig1-dev
libfontenc-dev
libfreeimage-dev
libfreetype6-dev
libfs-dev
libgdk-pixbuf2.0-dev
libgl1-mesa-dev
libglew1.5-dev
libglfw-dev
libglib2.0-dev
libglibmm-2.4-dev
libglu1-mesa-dev
libgsl0-dev
libgtk2.0-dev
libgtkglext1-dev
libgtkglextmm-x11-1.2-dev
libgtkmm-2.4-dev
libice-dev
libjpeg-dev
libjpeg-turbo8-dev
libjpeg8-dev
liblcms1-dev
libltdl-dev
liblua5.1-0-dev
libmad0-dev
libmikmod2-dev
libmng-dev
libncurses5-dev
libogg-dev
libogre-dev
libois-dev
libopenal-dev
libpango1.0-dev
libpangomm-1.4-dev
libpciaccess-dev
libpcre3-dev
libpixman-1-dev
libpng12-dev
libpthread-stubs0-dev
libpulse-dev
libqt4-dev
libqt4-opengl-dev
libqtwebkit-dev
libreadline-dev
libreadline6-dev
libsdl-image1.2-dev
libsdl-mixer1.2-dev
libsdl-net1.2-dev
libsdl1.2-dev
libsigc++-2.0-dev
libslang2-dev
libsm-dev
libssl-dev
libstdc++6-4.6-dev
libswscale-dev
libtiff4-dev
libtinfo-dev
libusb-1.0-0-dev
libusb-dev
libvorbis-dev
libwxbase2.8-dev
libwxgtk2.8-dev
libx11-dev
libxau-dev
libxaw7-dev
libxcb-render0-dev
libxcb-shm0-dev
libxcb1-dev
libxcomposite-dev
libxcursor-dev
libxdamage-dev
libxdmcp-dev
libxext-dev
libxfixes-dev
libxfont-dev
libxft-dev
libxi-dev
libxinerama-dev
libxkbfile-dev
libxmu-dev
libxmuu-dev
libxpm-dev
libxrandr-dev
libxrender-dev
libxres-dev
libxss-dev
libxt-dev
libxtst-dev
libxv-dev
libxvmc-dev
libxxf86dga-dev
libxxf86vm-dev
libzzip-dev
linux-libc-dev
manpages-dev
mesa-common-dev
python-dbus-dev
python2.7-dev
qt4-dev-tools
x11proto-bigreqs-dev
x11proto-composite-dev
x11proto-core-dev
x11proto-damage-dev
x11proto-dmx-dev
x11proto-dri2-dev
x11proto-fixes-dev
x11proto-fonts-dev
x11proto-gl-dev
x11proto-input-dev
x11proto-kb-dev
x11proto-randr-dev
x11proto-record-dev
x11proto-render-dev
x11proto-resource-dev
x11proto-scrnsaver-dev
x11proto-video-dev
x11proto-xcmisc-dev
x11proto-xext-dev
x11proto-xf86bigfont-dev
x11proto-xf86dga-dev
x11proto-xf86dri-dev
x11proto-xf86vidmode-dev
x11proto-xinerama-dev
xorg-dev
xserver-xorg-dev
xtrans-dev
zlib1g-dev

```Thanks in advance.


Edit 2:
Problem solved:)
It turns out i just had to link these libs from /usr/lib/i386-linux-gnu/ to /usr/lib/

```
libGL.so
libGLU.so
libQtCore.so
libQtGui.so
libQtOpenGL.so
libz.so
```Polyworld builds and runs fine.

Cheers.

---

