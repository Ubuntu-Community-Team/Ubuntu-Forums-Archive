---
title: "getting an Ogre exception trying to build funguloids with code blocks."
date: 2011-05-06
forum: Programming Talk
---

### Post by Jonas thomas on 2011-05-06
I've managed to get funguloids to build but its throwing an ogre exception when it's starts to run.. He's what I'm getting.

> Creating resource group General
Creating resource group Internal
Creating resource group Autodetect
SceneManagerFactory for type 'DefaultSceneManager' registered.
Registering ResourceManager for type Material
Registering ResourceManager for type Mesh
Registering ResourceManager for type Skeleton
MovableObjectFactory for type 'ParticleSystem' registered.
OverlayElementFactory for type Panel registered.
OverlayElementFactory for type BorderPanel registered.
OverlayElementFactory for type TextArea registered.
Registering ResourceManager for type Font
ArchiveFactory for archive type FileSystem registered.
ArchiveFactory for archive type Zip registered.
DDS codec registering
FreeImage version: 3.10.0
This program uses FreeImage, a free, open source image library supporting all common bitmap formats. See [http://freeimage.sourceforge.net](http://freeimage.sourceforge.net) for details
Supported formats: bmp,ico,jpg,jif,jpeg,jpe,jng,koa,iff,lbm,mng,pbm,pbm,pcd,pcx,pgm,pgm,png,ppm,ppm,ras,tga,targa,tif,tiff,wap,wbmp,wbm,psd,cut,xbm,xpm,gif,hdr,g3,sgi,exr,j2k,j2c,jp2
Registering ResourceManager for type HighLevelGpuProgram
Registering ResourceManager for type Compositor
MovableObjectFactory for type 'Entity' registered.
MovableObjectFactory for type 'Light' registered.
MovableObjectFactory for type 'BillboardSet' registered.
MovableObjectFactory for type 'ManualObject' registered.
MovableObjectFactory for type 'BillboardChain' registered.
MovableObjectFactory for type 'RibbonTrail' registered.
${datarootdir}/funguloids/plugins.cfg not found, automatic plugin loading disabled.
*-*-* OGRE Initialising
*-*-* Version 1.7.2 (Cthugha)
**An exception has occured: OGRE EXCEPTION(6:FileNotFoundException): '${datarootdir}/funguloids/plugins.cfg' file not found! in ConfigFile::load at /home/jonas/dev/ogre/ogre_src_v1-7-2/OgreMain/src/OgreConfigFile.cpp (line 83)**codeBlockFungoliods: /usr/local/include/OGRE/OgreSharedPtr.h:160: T* Ogre::SharedPtr<T>::operator->() const [with T = Ogre::Material]: Assertion `pRep' failed.
Aborted

Process returned 134 (0x86)   execution time : 1.239 s
Press ENTER to continue.

So its looking for plugins.cfg

Here's what I got as far as plugins.cfg ....
> jonas@jonas5:~$ locate plugins.cfg
/etc/OGRE/plugins.cfg
/etc/OGRE/plugins.cfg.cgprogrammanager
/home/jonas/.local/share/Trash/files/funguloids/bin/plugins.cfg.in
/home/jonas/.local/share/Trash/files/ogre_build/bin/plugins.cfg
/home/jonas/.local/share/Trash/files/ogre_build/inst/bin/release/plugins.cfg
/home/jonas/.local/share/Trash/files/ogre_src_v1-7-2/CMake/Templates/plugins.cfg.in
/home/jonas/.local/share/Trash/files/ogre_src_v1-7-2/SDK/OSX/Xcode Templates/Xcode/Project Templates/Ogre/Mac OS X/Resources/plugins.cfg
/home/jonas/.local/share/Trash/files/ogre_src_v1-7-2/Tools/MaterialEditor/bin/Debug/plugins.cfg
/home/jonas/.local/share/Trash/files/ogre_src_v1-7-2/Tools/MaterialEditor/bin/Release/plugins.cfg
/home/jonas/dev/ogre/ogre_src_v1-7-2/CMake/Templates/plugins.cfg.in
/home/jonas/dev/ogre/ogre_src_v1-7-2/SDK/OSX/Xcode Templates/Xcode/Project Templates/Ogre/Mac OS X/Resources/plugins.cfg
/home/jonas/dev/ogre/ogre_src_v1-7-2/Tools/MaterialEditor/bin/Debug/plugins.cfg
/home/jonas/dev/ogre/ogre_src_v1-7-2/Tools/MaterialEditor/bin/Release/plugins.cfg
/home/jonas/dev/ogre_build/bin/plugins.cfg
/home/jonas/dev/ogre_build/inst/bin/release/plugins.cfg
/home/jonas/funguloids/bin/plugins.cfg
/home/jonas/funguloids/bin/plugins.cfg.in
/home/jonas/junktestOgre/Junktest/plugins.cfg
/usr/local/share/OGRE/plugins.cfg
/usr/local/share/funguloids/plugins.cfg
jonas@jonas5:~$ 


Sooo... 

```
namespace Ogre {

    //-----------------------------------------------------------------------
    ConfigFile::ConfigFile()
    {
    }
    //-----------------------------------------------------------------------
    ConfigFile::~ConfigFile()
    {
        SettingsBySection::iterator seci, secend;
        secend = mSettings.end();
        for (seci = mSettings.begin(); seci != secend; ++seci)
        {
            OGRE_DELETE_T(seci->second, SettingsMultiMap, MEMCATEGORY_GENERAL);
        }
    }
    //-----------------------------------------------------------------------
    void ConfigFile::clear(void)
    {
        for (SettingsBySection::iterator seci = mSettings.begin(); 
            seci != mSettings.end(); ++seci)
        {
             OGRE_DELETE_T(seci->second, SettingsMultiMap, MEMCATEGORY_GENERAL);
        }
        mSettings.clear();
    }
    //-----------------------------------------------------------------------
    void ConfigFile::load(const String& filename, const String& separators, bool trimWhitespace)
    {
        loadDirect(filename, separators, trimWhitespace);
    }
    //-----------------------------------------------------------------------
    void ConfigFile::load(const String& filename, const String& resourceGroup, 
        const String& separators, bool trimWhitespace)
    {
		loadFromResourceSystem(filename, resourceGroup, separators, trimWhitespace);
    }
	//-----------------------------------------------------------------------
	void ConfigFile::loadDirect(const String& filename, const String& separators, 
		bool trimWhitespace)
	{
		/* Open the configuration file */
		std::ifstream fp;
 [B]       // Always open in binary mode
		fp.open(filename.c_str(), std::ios::in | std::ios::binary);
		if(!fp)
			OGRE_EXCEPT(
			Exception::ERR_FILE_NOT_FOUND, "'" + filename + "' file not found!", "ConfigFile::load" );
[/B]
		// Wrap as a stream
		DataStreamPtr stream(OGRE_NEW FileStreamDataStream(filename, &fp, false));

#if OGRE_PLATFORM == OGRE_PLATFORM_SYMBIAN
		// seems readLine doesn't work correctly in SYMBIAN with files
		DataStreamPtr memoryStream(OGRE_NEW MemoryDataStream(stream));
		stream = memoryStream;
#endif

		load(stream, separators, trimWhitespace);

	}
	//-----------------------------------------------------------------------
	void ConfigFile::loadFromResourceSystem(const String& filename, 
		const String& resourceGroup, const String& separators, bool trimWhitespace)
	{
		DataStreamPtr stream = 
			ResourceGroupManager::getSingleton().openResource(filename, resourceGroup);
		load(stream, separators, trimWhitespace);
	}
    //-----------------------------------------------------------------------
    void ConfigFile::load(const DataStreamPtr& stream, const String& separators, 
        bool trimWhitespace)
    {
        /* Clear current settings map */
        clear();

        String currentSection = StringUtil::BLANK;
        SettingsMultiMap* currentSettings = OGRE_NEW_T(SettingsMultiMap, MEMCATEGORY_GENERAL)();
        mSettings[currentSection] = currentSettings;


        /* Process the file line for line */
        String line, optName, optVal;
        while (!stream->eof())
        {
            line = stream->getLine();
            /* Ignore comments & blanks */
            if (line.length() > 0 && line.at(0) != '#' && line.at(0) != '@')
            {
                if (line.at(0) == '[' && line.at(line.length()-1) == ']')
                {
                    // Section
                    currentSection = line.substr(1, line.length() - 2);
					SettingsBySection::const_iterator seci = mSettings.find(currentSection);
					if (seci == mSettings.end())
					{
						currentSettings = OGRE_NEW_T(SettingsMultiMap, MEMCATEGORY_GENERAL)();
						mSettings[currentSection] = currentSettings;
					}
					else
					{
						currentSettings = seci->second;
					} 
                }
                else
                {
                    /* Find the first seperator character and split the string there */
					Ogre::String::size_type separator_pos = line.find_first_of(separators, 0);
                    if (separator_pos != Ogre::String::npos)
                    {
                        optName = line.substr(0, separator_pos);
                        /* Find the first non-seperator character following the name */
                        Ogre::String::size_type nonseparator_pos = line.find_first_not_of(separators, separator_pos);
                        /* ... and extract the value */
                        /* Make sure we don't crash on an empty setting (it might be a valid value) */
                        optVal = (nonseparator_pos == Ogre::String::npos) ? "" : line.substr(nonseparator_pos);
                        if (trimWhitespace)
                        {
                            StringUtil::trim(optVal);
                            StringUtil::trim(optName);
                        }
                        currentSettings->insert(SettingsMultiMap::value_type(optName, optVal));
                    }
                }
            }
        }
    }
    //-----------------------------------------------------------------------
    String ConfigFile::getSetting(const String& key, const String& section, const String& defaultValue) const
    {
        
        SettingsBySection::const_iterator seci = mSettings.find(section);
        if (seci == mSettings.end())
        {
            return defaultValue;
        }
        else
        {
            SettingsMultiMap::const_iterator i = seci->second->find(key);
            if (i == seci->second->end())
            {
                return defaultValue;
            }
            else
            {
                return i->second;
            }
        }
    }
    //-----------------------------------------------------------------------
    StringVector ConfigFile::getMultiSetting(const String& key, const String& section) const
    {
        StringVector ret;


        SettingsBySection::const_iterator seci = mSettings.find(section);
        if (seci != mSettings.end())
        {
            SettingsMultiMap::const_iterator i;

            i = seci->second->find(key);
            // Iterate over matches
            while (i != seci->second->end() && i->first == key)
            {
                ret.push_back(i->second);
                ++i;
            }
        }
        return ret;


    }
    //-----------------------------------------------------------------------
    ConfigFile::SettingsIterator ConfigFile::getSettingsIterator(const String& section)
    {
        SettingsBySection::const_iterator seci = mSettings.find(section);
        if (seci == mSettings.end())
        {
            OGRE_EXCEPT(Exception::ERR_ITEM_NOT_FOUND, 
                "Cannot find section " + section, 
                "ConfigFile::getSettingsIterator");
        }
        else
        {
            return SettingsIterator(seci->second->begin(), seci->second->end());
        }
    }
    //-----------------------------------------------------------------------
    ConfigFile::SectionIterator ConfigFile::getSectionIterator(void)
    {
        return SectionIterator(mSettings.begin(), mSettings.end());
    }

}
```

Soo... I think what's going on is that funguloids must be jazzing the file path up.. Any thoughts??

---

### Post by Jonas thomas on 2011-05-06
Ok.. this is making more sense to me..

src/ogreapp.cpp
> // Setup
bool OgreApplication::setup() {
	// Create Ogre root
	mRoot = new Root(
			String(OGRE_PLUGINS_AND_RESOURCES_PATH) + "plugins.cfg",
			OGRE_CONFIG_AND_LOG_PATH + "ogre.cfg",
			OGRE_CONFIG_AND_LOG_PATH + "Ogre.log"
			);

	ConfigFile cfg;
	cfg.load(String(OGRE_PLUGINS_AND_RESOURCES_PATH) + "plugins.cfg");
	String pluginDir = cfg.getSetting("PluginFolder");
	struct stat sb;
	if (stat((pluginDir + "Plugin_CgProgramManager.so").c_str(), &sb) == 0)
		mRoot->loadPlugin(pluginDir + "Plugin_CgProgramManager");

	// Random seed
	srand(time(NULL));

	// Add the MPK archive support
	mMPakFactory = new MPakArchiveFactory();
	ArchiveManager::getSingleton().addArchiveFactory(mMPakFactory);

	// Load resource paths from config file
	ConfigFile cf;
	**cf.load(String(OGRE_PLUGINS_AND_RESOURCES_PATH) + "resources.cfg");**

OGRE_PLUGINS_AND_RESOURCES_PATH is defined in include/config.h
> /* Define to 1 if the system has the type `_Bool'. */
#define HAVE__BOOL 1

/* That's where plugins.cfg and resources.cfg are installed */
#define OGRE_PLUGINS_AND_RESOURCES_PATH "**${datarootdir}**/funguloids/"


Soo... I suppose hack ${datarootdir} and replace it with an absolute path... But I'm thinking that there's probably a way to set it in the code::blocks project file... Right???

---

### Post by Jonas thomas on 2011-05-06
Ok a little googling..

[http://www.gnu.org/software/hello/manual/autoconf/Changed-Directory-Variables.html]("http://www.gnu.org/software/hello/manual/autoconf/Changed-Directory-Variables.html")
I think that has to do with when 
./configure 
make
sudo make install
is run with code originally downloaded.. Right.. Here's where I'm fuzzy.. 
Does that process replace that? The program failed which is why I went to code::blocks.  This is terra incognito for me.. I can hack my way past but what is the "correct way" to address this at this point?

---

### Post by Jonas thomas on 2011-05-06
Ah.... I hacked it up... To move things.. Along..
Now.. I get this..

> Creating resource group General
Creating resource group Internal
Creating resource group Autodetect
SceneManagerFactory for type 'DefaultSceneManager' registered.
Registering ResourceManager for type Material
Registering ResourceManager for type Mesh
Registering ResourceManager for type Skeleton
MovableObjectFactory for type 'ParticleSystem' registered.
OverlayElementFactory for type Panel registered.
OverlayElementFactory for type BorderPanel registered.
OverlayElementFactory for type TextArea registered.
Registering ResourceManager for type Font
ArchiveFactory for archive type FileSystem registered.
ArchiveFactory for archive type Zip registered.
DDS codec registering
FreeImage version: 3.10.0
This program uses FreeImage, a free, open source image library supporting all common bitmap formats. See [http://freeimage.sourceforge.net](http://freeimage.sourceforge.net) for details
Supported formats: bmp,ico,jpg,jif,jpeg,jpe,jng,koa,iff,lbm,mng,pbm,pbm,pcd,pcx,pgm,pgm,png,ppm,ppm,ras,tga,targa,tif,tiff,wap,wbmp,wbm,psd,cut,xbm,xpm,gif,hdr,g3,sgi,exr,j2k,j2c,jp2
Registering ResourceManager for type HighLevelGpuProgram
Registering ResourceManager for type Compositor
MovableObjectFactory for type 'Entity' registered.
MovableObjectFactory for type 'Light' registered.
MovableObjectFactory for type 'BillboardSet' registered.
MovableObjectFactory for type 'ManualObject' registered.
MovableObjectFactory for type 'BillboardChain' registered.
MovableObjectFactory for type 'RibbonTrail' registered.
Loading library /usr/lib/OGRE/RenderSystem_GL
Installing plugin: GL RenderSystem
OpenGL Rendering Subsystem created.
Plugin successfully installed
Loading library /usr/lib/OGRE/Plugin_ParticleFX
Installing plugin: ParticleFX
Particle Emitter Type 'Point' registered
Particle Emitter Type 'Box' registered
Particle Emitter Type 'Ellipsoid' registered
Particle Emitter Type 'Cylinder' registered
Particle Emitter Type 'Ring' registered
Particle Emitter Type 'HollowEllipsoid' registered
Particle Affector Type 'LinearForce' registered
Particle Affector Type 'ColourFader' registered
Particle Affector Type 'ColourFader2' registered
Particle Affector Type 'ColourImage' registered
Particle Affector Type 'ColourInterpolator' registered
Particle Affector Type 'Scaler' registered
Particle Affector Type 'Rotator' registered
Particle Affector Type 'DirectionRandomiser' registered
Particle Affector Type 'DeflectorPlane' registered
Plugin successfully installed
Loading library /usr/lib/OGRE/Plugin_OctreeSceneManager
Installing plugin: Octree & Terrain Scene Manager
Plugin successfully installed
*-*-* OGRE Initialising
*-*-* Version 1.7.2 (Cthugha)
Loading library /usr/lib/OGRE/Plugin_CgProgramManager
Installing plugin: Cg Program Manager
Plugin successfully installed
ArchiveFactory for archive type MPK registered.
Creating resource group Bootstrap
Added resource location '/usr/local/share/funguloids/bootstrap.mpk' of type 'MPK' to resource group 'Bootstrap'
Added resource location '/usr/local/share/funguloids/music' of type 'FileSystem' to resource group 'General'
Added resource location '/usr/local/share/funguloids/icon' of type 'FileSystem' to resource group 'General'
Added resource location '/usr/local/share/funguloids/funguloids.mpk' of type 'MPK' to resource group 'General'
CPU Identifier & Features
-------------------------
 *   CPU ID: GenuineIntel: Intel(R) Pentium(R) 4 CPU 3.40GHz
 *      SSE: yes
 *     SSE2: yes
 *     SSE3: yes
 *      MMX: yes
 *   MMXEXT: yes
 *    3DNOW: no
 * 3DNOWEXT: no
 *     CMOV: yes
 *      TSC: yes
 *      FPU: yes
 *      PRO: yes
 *       HT: yes
-------------------------
******************************
*** Starting GLX Subsystem ***
******************************
GLRenderSystem::_createRenderWindow "Those Funny Funguloids!", 1920x1080 fullscreen  miscParams: FSAA=0 displayFrequency=50 MHz gamma=No vsync=No 
Segmentation fault

Process returned 139 (0x8B)   execution time : 2.531 s
Press ENTER to continue.


> // Game title
const String GameApplication::getTitle() const {
	return "Those Funny Funguloids!";
}


> 

// Setup
bool OgreApplication::setup() {
	// Create Ogre root
	mRoot = new Root(
			String(OGRE_PLUGINS_AND_RESOURCES_PATH) + "plugins.cfg",
			OGRE_CONFIG_AND_LOG_PATH + "ogre.cfg",
			OGRE_CONFIG_AND_LOG_PATH + "Ogre.log"
			);

	ConfigFile cfg;
	cfg.load(String(OGRE_PLUGINS_AND_RESOURCES_PATH) + "plugins.cfg");
	String pluginDir = cfg.getSetting("PluginFolder");
	struct stat sb;
	if (stat((pluginDir + "Plugin_CgProgramManager.so").c_str(), &sb) == 0)
		mRoot->loadPlugin(pluginDir + "Plugin_CgProgramManager");

	// Random seed
	srand(time(NULL));

	// Add the MPK archive support
	mMPakFactory = new MPakArchiveFactory();
	ArchiveManager::getSingleton().addArchiveFactory(mMPakFactory);

	// Load resource paths from config file
	ConfigFile cf;
	cf.load(String(OGRE_PLUGINS_AND_RESOURCES_PATH) + "resources.cfg");

	// Parse the resources.cfg
	ConfigFile::SectionIterator seci = cf.getSectionIterator();

	String secName, typeName, archName;
	while(seci.hasMoreElements()) {
		secName = seci.peekNextKey();
		ConfigFile::SettingsMultiMap *settings = seci.getNext();
		ConfigFile::SettingsMultiMap::iterator i;
		for(i = settings->begin(); i != settings->end(); ++i) {
			typeName = i->first;
			archName = i->second;
			ResourceGroupManager::getSingleton().addResourceLocation(archName, typeName, secName);
		}
	}


	// Get the configuration
	if(!mRoot->restoreConfig())
		if(!mRoot->showConfigDialog())
			return false;

	// Initialise the system
	**mWindow = mRoot->initialise(true, getTitle().c_str());**



> // Base class for an Ogre application.
class OgreApplication {
public:
	OgreApplication() {
		mFrameListener = 0;
		mRoot = 0;
	}
	virtual ~OgreApplication();


	// Start the application
	virtual void start() {
		if(!setup())
			return;

		mRoot->startRendering();

		// Clean up
		destroyScene();
	}


	// Returns the window title
	virtual const String getTitle() const {
		return "OgreApplication";
	}

	Root *getRoot() const { return mRoot; }
	RenderWindow *getRenderWindow() const { return mWindow; }

protected:
	**Root *mRoot;**
	Camera *mCamera;
	SceneManager *mSceneMgr;
	RenderWindow *mWindow;
	OgreAppFrameListener *mFrameListener;
	class MPakArchiveFactory *mMPakFactory;

	// Sets up the application, returns false if the user cancels
	virtual bool setup();

	// Create the scene
	virtual void createScene() = 0;

	// Destroy the scene
    virtual void destroyScene() { }

	// Create the scene manager
	virtual void createSceneManager() {
		mSceneMgr = mRoot->createSceneManager(ST_GENERIC);
	}

	// Create the frame listener
	virtual void createFrameListener() {
        mFrameListener = new OgreAppFrameListener(this, mWindow, mCamera, NULL, mSceneMgr, NULL);
        mRoot->addFrameListener(mFrameListener);
	}

	// Create the camera
	virtual void createCamera() {
		mCamera = mSceneMgr->createCamera("PlayerCam");
		mCamera->setPosition(Vector3(0,0,500));
		mCamera->lookAt(Vector3(0,0,-300));
		mCamera->setNearClipDistance(5);
	}

    // Create the viewport
	virtual void createViewport() {
		Viewport *vp = mWindow->addViewport(mCamera);
		vp->setBackgroundColour(ColourValue(0,0,0));
		mCamera->setAspectRatio(Real(vp->getActualWidth()) / Real(vp->getActualHeight()));
	}

};


#endif



> /*
-----------------------------------------------------------------------------
This source file is part of OGRE
    (Object-oriented Graphics Rendering Engine)
For the latest info, see [http://www.ogre3d.org/](http://www.ogre3d.org/)

Copyright (c) 2000-2009 Torus Knot Software Ltd

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
-----------------------------------------------------------------------------
*/
#ifndef __ROOT__
#define __ROOT__

// Precompiler options
#include "OgrePrerequisites.h"

#include "OgreSingleton.h"
#include "OgreString.h"
#include "OgreSceneManagerEnumerator.h"
#include "OgreResourceGroupManager.h"
#include "OgreLodStrategyManager.h"
#include "OgreWorkQueue.h"

#include <exception>

namespace Ogre
{
	/** \addtogroup Core
	*  @{
	*/
	/** \addtogroup General
	*  @{
	*/

    typedef vector<RenderSystem*>::type RenderSystemList;
	
    /** The root class of the Ogre system.
        @remarks
            The Ogre::Root class represents a starting point for the client
            application. From here, the application can gain access to the
            fundamentals of the system, namely the rendering systems
            available, management of saved configurations, logging, and
            access to other classes in the system. Acts as a hub from which
            all other objects may be reached. An instance of Root must be
            created before any other Ogre operations are called. Once an
            instance has been created, the same instance is accessible
            throughout the life of that object by using Root::getSingleton
            (as a reference) or Root::getSingletonPtr (as a pointer).
    */
    class _OgreExport **Root** : public Singleton<Root>, public RootAlloc
    {
        // To allow update of active renderer if
        // RenderSystem::initialise is used directly
        friend class RenderSystem;
	protected:
        RenderSystemList mRenderers;
        RenderSystem* mActiveRenderer;
        String mVersion;
		String mConfigFileName;
	    bool mQueuedEnd;
        // In case multiple render windows are created, only once are the resources loaded.
        bool mFirstTimePostWindowInit;


Hmmm... Now I'm really stumped.  I suppose set a break point.. or do some googling...  Really should be studying for my C++ final.... Time for bed..

---

### Post by Jonas thomas on 2011-05-07
Ok.. This is more exiting that looking at binary search trees...

I managed to drill down to OgreeRoot.CPP and found where the segmentation fault is occurring.
>     //-----------------------------------------------------------------------
    RenderWindow* Root::initialise(bool autoCreateWindow, const String& windowTitle, const String& customCapabilitiesConfig)
    {
        if (!mActiveRenderer)
            OGRE_EXCEPT(Exception::ERR_INVALID_STATE,
            "Cannot initialise - no render "
            "system has been selected.", "Root::initialise");

        if (!mControllerManager)
            mControllerManager = OGRE_NEW ControllerManager();

        // .rendercaps manager
        RenderSystemCapabilitiesManager& rscManager = RenderSystemCapabilitiesManager::getSingleton();
        // caller wants to load custom RenderSystemCapabilities form a config file
        if(customCapabilitiesConfig != StringUtil::BLANK)
        {
            ConfigFile cfg;
            cfg.load(customCapabilitiesConfig, "\t:=", false);

            // Capabilities Database setting must be in the same format as
            // resources.cfg in Ogre examples.
            ConfigFile::SettingsIterator iter = cfg.getSettingsIterator("Capabilities Database");
            while(iter.hasMoreElements())
            {
                String archType = iter.peekNextKey();
                String filename = iter.getNext();

                rscManager.parseCapabilitiesFromArchive(filename, archType, true);
            }

            String capsName = cfg.getSetting("Custom Capabilities");
            // The custom capabilities have been parsed, let's retrieve them
            RenderSystemCapabilities* rsc = rscManager.loadParsedCapabilities(capsName);
            if(rsc == 0)
            {
                OGRE_EXCEPT(Exception::ERR_ITEM_NOT_FOUND,
                    String("Cannot load a RenderSystemCapability named ") + capsName,
                    "Root::initialise");
            }

            // Tell RenderSystem to use the comon rsc
            useCustomRenderSystemCapabilities(rsc);
        }


        PlatformInformation::log(LogManager::getSingleton().getDefaultLog());
        **mAutoWindow =  mActiveRenderer->_initialise(autoCreateWindow, windowTitle);**


        if (autoCreateWindow && !mFirstTimePostWindowInit)
        {
            oneTimePostWindowInit();
            mAutoWindow->_setPrimary();
        }

        // Initialise timer
        mTimer->reset();

        // Init pools
        ConvexBody::_initialisePool();

        mIsInitialised = true;

        return mAutoWindow;

    }
The call stack looks like this:
```
#0 0xb6e17db2    std::string::compare(std::string const&) const() (/usr/lib/libstdc++.so.6?)
#1 0x8065415    std:perator< <char, std::char_traits<char>, std::allocator<char> >(__lhs=..., __rhs=...) (/usr/include/c++/4.4/bits/basic_string.h:2320)
#2 0x806552a    std::less<std::string>:perator() (this=0xb7fd9364, __x=..., __y=...) (/usr/include/c++/4.4/bits/stl_function.h:230)
#3 0xb79ba76e    std::_Rb_tree<std::string, std:air<std::string const, Ogre::Codec*>, std::_Select1st<std:air<std::string const, Ogre::Codec*> >, std::less<std::string>, Ogre::STLAllocator<std::pair<std::string const, Ogre::Codec*>, Ogre::CategorisedAllocPolicy<(Ogre::MemoryCategory)0> > >::_M_lower_bound(this=0xb7fd9360, __x=0xb7fd9364, __y=0xb7fd9368, __k=...) (/usr/include/c++/4.4/bits/stl_tree.h:986)
#4 0xb79ba046    std::_Rb_tree<std::string, std::pair<std::string const, Ogre::Codec*>, std::_Select1st<std::pair<std::string const, Ogre::Codec*> >, std::less<std::string>, Ogre::STLAllocator<std:air<std::string const, Ogre::Codec*>, Ogre::CategorisedAllocPolicy<(Ogre::MemoryCategory)0> > >::find(this=0xb7fd9360, __k=...) (/usr/include/c++/4.4/bits/stl_tree.h:1421)
#5 0xb79b9cac    std::map<std::string, Ogre::Codec*, std::less<std::string>, Ogre::STLAllocator<std:air<std::string const, Ogre::Codec*>, Ogre::CategorisedAllocPolicy<(Ogre::MemoryCategory)0> > >::find(this=0xb7fd9360, __x=...) (/usr/include/c++/4.4/bits/stl_map.h:659)
#6 0xb79b9512    Ogre::Codec::getCodec(extension=...) (/home/jonas/dev/ogre/ogre_src_v1-7-2/OgreMain/src/OgreCodec.cpp:57)
#7 0xb7a76627    Ogre::Image::load(this=0xbffff0b4, stream=..., type=...) (/home/jonas/dev/ogre/ogre_src_v1-7-2/OgreMain/src/OgreImage.cpp:387)
#8 0xb7a7579e    Ogre::Image::load(this=0xbffff0b4, strFileName=..., group=...) (/home/jonas/dev/ogre/ogre_src_v1-7-2/OgreMain/src/OgreImage.cpp:307)
#9 0xb4a77411    Ogre::GLXGLSupport::loadIcon(this=0x8125db0, name=..., pixmap=0x81ab3f4, bitmap=0x81ab404) (OgreGLXGLSupport.cpp:68
#10 0xb4a82f6e    Ogre::GLXWindow::create(this=0xb444ecc0, name=..., width=1920, height=1080, fullScreen=true, miscParams=0xbffff56 (OgreGLXWindow.cpp:360)
#11 0xb4a77d04    Ogre::GLXGLSupport::newWindow(this=0x8125db0, name=..., width=1920, height=1080, fullScreen=true, miscParams=0xbffff56 (OgreGLXGLSupport.cpp:380)
#12 0xb4a4a1c5    Ogre::GLRenderSystem::_createRenderWindow(this=0xb444e278, name=..., width=1920, height=1080, fullScreen=<value optimized out>, miscParams=0xbffff56 (OgreGLRenderSystem.cpp:975)
#13 0xb4a78abb    Ogre::GLXGLSupport::createWindow(this=0x8125db0, autoCreateWindow=true, renderSystem=0xb444e278, windowTitle=...) (OgreGLXGLSupport.cpp:369)
#14 0xb4a41482    Ogre::GLRenderSystem::_initialise(this=0xb444e278, autoCreateWindow=true, windowTitle=...) (OgreGLRenderSystem.cpp:194)
#15 0xb7c62c7e    Ogre::Root::initialise(this=0xb570b260, autoCreateWindow=true, windowTitle=..., customCapabilitiesConfig=...) (/home/jonas/dev/ogre/ogre_src_v1-7-2/OgreMain/src/OgreRoot.cpp:667)
#16 0x807a19c    OgreApplication::setup(this=0xbffff880) (/home/jonas/funguloids/src/ogreapp.cpp:115)
#17 0x8061fe4    OgreApplication::start(this=0xbffff880) (../include/ogreapp.h:4
#18 0x8065b87    main(argc=1, argv=0xbffff984) (/home/jonas/funguloids/src/main.cpp:50)[/QUOTE]I think the problem has do with this:
OgreCodec.Cpp
>     Codec* Codec::getCodec(const String& extension)
    {
        String lwrcase = extension;
        StringUtil::toLowerCase(lwrcase);
        **CodecList::const_iterator i = ms_mapCodecs.find(lwrcase);**
        if (i == ms_mapCodecs.end())
        {
            String formats_str;
            if(ms_mapCodecs.empty())
                formats_str = "There are no formats supported (no codecs registered).";
            else
                formats_str = "Supported formats are: " + StringConverter::toString(getExtensions()) + ".";

            OGRE_EXCEPT(Exception::ERR_ITEM_NOT_FOUND, 
                "Can not find codec for '" + extension + "' image format.\n" + 
                formats_str,
                "Codec::getCodec");
        }

        return i->second;

    }

```It seems like the segmentation fault is occurring in 
basic_string.h
 [QUOTE]// operator <
  /**
   *  @brief  Test if string precedes string.
   *  @param lhs  First string.
   *  @param rhs  Second string.
   *  @return  True if @a lhs precedes @a rhs.  False otherwise.
   */
  template<typename _CharT, typename _Traits, typename _Alloc>
    inline bool
    operator<(const basic_string<_CharT, _Traits, _Alloc>& __lhs,
          const basic_string<_CharT, _Traits, _Alloc>& __rhs)
    **{ return __lhs.compare(__rhs) < 0; }**

  /**
   *  @brief  Test if string precedes C string.
   *  @param lhs  String.
   *  @param rhs  C string.
   *  @return  True if @a lhs precedes @a rhs.  False otherwise.
   */I found a little info here..[URL="http://www.ogre3d.org/forums/viewtopic.php?f=2&t=11060"]
http://www.ogre3d.org/forums/viewtopic.php?f=2&t=11060[/URL]


Ok...
Looking at some of the data here.


> Image & Image::load(const String& strFileName, const String& group)
    {

        String strExt;

        size_t pos = strFileName.find_last_of(".");
        if( pos != String::npos && pos < (strFileName.length() - 1))
        {
            strExt = strFileName.substr(pos+1);
        }

        DataStreamPtr encoded = ResourceGroupManager::getSingleton().openResource(strFileName, group);
        **return load(encoded, strExt);**

    }Lets see...
strFilename = "GLX_icon.png"
strExt = "png"
Hmmm. > 
jonas@jonas5:~$ locate GLX_icon.png
/home/jonas/.local/share/Trash/files/funguloids/bin/icon/GLX_icon.png
/home/jonas/.local/share/Trash/files/ogre_src_v1-7-2/Samples/Media/materials/textures/GLX_icon.png
/home/jonas/dev/ogre/ogre_src_v1-7-2/Samples/Media/materials/textures/GLX_icon.png
/home/jonas/funguloids/bin/icon/GLX_icon.png
/usr/local/share/OGRE/media/materials/textures/GLX_icon.png
/usr/local/share/funguloids/icon/GLX_icon.png
jonas@jonas5:~$ Hmm.. I wonder if that issue might be if there might not be a full file path...
Ok... Back to studying binary search trees..

---

