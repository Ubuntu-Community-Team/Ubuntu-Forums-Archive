---
title: "cannot allocate an object of abstract type ‘MPakArchive’"
date: 2011-05-05
forum: Programming Talk
---

### Post by Jonas thomas on 2011-05-05
I've been trying playing around trying to get this funguloids source code to work for my 8 year old(where I really should be studying for my C++ final).  I think the issue is that the virtual functions defined in the base class need to be implemented.. Am I interpreting the error message correctly?
Is it possible that Ogre added =0 to the virtual functions in Archive which broke funguloids? (scary... I think I almost know what I'm talking about. (I just want to know I'm on the correct track here.)



```


/home/jonas/funguloids/src/game.cpp||In member function ‘void GameApplication::endGame()’:|
/home/jonas/funguloids/src/game.cpp|253|warning: deprecated conversion from string constant to ‘char*’|
/home/jonas/funguloids/src/mpakogre.cpp|88|warning: "/*" within comment|
../include/mpakogre.h||In member function ‘virtual Ogre::Archive* MPakArchiveFactory::createInstance(const Ogre::String&)’:|
../include/mpakogre.h|86|error: cannot allocate an object of abstract type ‘MPakArchive’|
../include/mpakogre.h|38|note:   because the following virtual functions are pure within ‘MPakArchive’:|
/usr/local/include/OGRE/OgreArchive.h|146|note: 	virtual Ogre::DataStreamPtr Ogre::Archive::open(const Ogre::String&, bool) const|
||=== Build finished: 1 errors, 2 warnings (0 minutes, 54 seconds) ===|
```

```
// Archive factory for MPK files
class MPakArchiveFactory : public ArchiveFactory {
public:
	MPakArchiveFactory() : ArchiveFactory() {}
	virtual ~MPakArchiveFactory() {}
	const String &getType(void) const;

	Archive *createInstance(const String &name) {
		**return new MPakArchive(name, "MPK");**//Compiler error here.
	}

	void destroyInstance(Archive *arch) { delete arch; }
};


```

```
// Archive class for reading from MPK files
class MPakArchive : public Archive {
protected:
	MPAK_FILE *mPakFile;
	FileInfoList mFileList;

public:
	MPakArchive(const String &name, const String &archType);
	~MPakArchive();

	bool isCaseSensitive(void) const { return true; }
	void load();
	void unload();

	DataStreamPtr open(const String &filename) const;
	StringVectorPtr list(bool recursive = true, bool dirs = false);
	FileInfoListPtr listFileInfo(bool recursive = true, bool dirs = false);

	StringVectorPtr find(const String &pattern, bool recursive = true, bool dirs = false);
	FileInfoListPtr findFileInfo(const String &pattern, bool recursive, bool dirs = false);

	bool exists(const String &filename);

	time_t getModifiedTime(const String& filename)
	{
		struct stat tagStat;
		bool ret = (stat(mName.c_str(), &tagStat) == 0);

		if (ret)
		{
			return tagStat.st_mtime;
		}
		else
		{
			return 0;
		}

	}
};

```


```
class _OgreExport Archive : public ArchiveAlloc
    {
    protected:
        /// Archive name
        String mName; 
        /// Archive type code
        String mType;
		/// Read-only flag
		bool mReadOnly;
    public:


        /** Constructor - don't call direct, used by ArchiveFactory.
        */
        Archive( const String& name, const String& archType )
            : mName(name), mType(archType), mReadOnly(true) {}

        /** Default destructor.
        */
        virtual ~Archive() {}

		/// Get the name of this archive
		const String& getName(void) const { return mName; }

        /// Returns whether this archive is case sensitive in the way it matches files
        virtual bool isCaseSensitive(void) const = 0;

        /** Loads the archive.
        @remarks
            This initializes all the internal data of the class.
        @warning
            Do not call this function directly, it is meant to be used
            only by the ArchiveManager class.
        */
        virtual void load() = 0;

        /** Unloads the archive.
        @warning
            Do not call this function directly, it is meant to be used
            only by the ArchiveManager class.
        */
        virtual void unload() = 0;

		/** Reports whether this Archive is read-only, or whether the contents
			can be updated. 
		*/
		virtual bool isReadOnly() const { return mReadOnly; }

        /** Open a stream on a given file. 
        @note
            There is no equivalent 'close' method; the returned stream
            controls the lifecycle of this file operation.
        @param filename The fully qualified name of the file
		@param readOnly Whether to open the file in read-only mode or not (note, 
			if the archive is read-only then this cannot be set to false)
        @returns A shared pointer to a DataStream which can be used to 
            read / write the file. If the file is not present, returns a null
			shared pointer.
        */
        virtual DataStreamPtr open(const String& filename, bool readOnly = true) const = 0;

		/** Create a new file (or overwrite one already there). 
		@note If the archive is read-only then this method will fail.
		@param filename The fully qualified name of the file
		@returns A shared pointer to a DataStream which can be used to 
		read / write the file. 
		*/
		virtual DataStreamPtr create(const String& filename) const
		{
                        (void)filename;
			OGRE_EXCEPT(Exception::ERR_NOT_IMPLEMENTED, 
				"This archive does not support creation of files.", 
				"Archive::create");
		}

		/** Delete a named file.
		@remarks Not possible on read-only archives
		@param filename The fully qualified name of the file
		*/
		virtual void remove(const String& filename) const
		{
                        (void)filename;
			OGRE_EXCEPT(Exception::ERR_NOT_IMPLEMENTED, 
				"This archive does not support removal of files.", 
				"Archive::remove");
		}

        /** List all file names in the archive.
        @note
            This method only returns filenames, you can also retrieve other
            information using listFileInfo.
        @param recursive Whether all paths of the archive are searched (if the 
            archive has a concept of that)
        @param dirs Set to true if you want the directories to be listed
            instead of files
        @returns A list of filenames matching the criteria, all are fully qualified
        */
        virtual StringVectorPtr list(bool recursive = true, bool dirs = false) = 0;
        
        /** List all files in the archive with accompanying information.
        @param recursive Whether all paths of the archive are searched (if the 
            archive has a concept of that)
        @param dirs Set to true if you want the directories to be listed
            instead of files
        @returns A list of structures detailing quite a lot of information about
            all the files in the archive.
        */
        virtual FileInfoListPtr listFileInfo(bool recursive = true, bool dirs = false) = 0;

        /** Find all file or directory names matching a given pattern
            in this archive.
        @note
            This method only returns filenames, you can also retrieve other
            information using findFileInfo.
        @param pattern The pattern to search for; wildcards (*) are allowed
        @param recursive Whether all paths of the archive are searched (if the 
            archive has a concept of that)
        @param dirs Set to true if you want the directories to be listed
            instead of files
        @returns A list of filenames matching the criteria, all are fully qualified
        */
        virtual StringVectorPtr find(const String& pattern, bool recursive = true,
            bool dirs = false) = 0;

        /** Find out if the named file exists (note: fully qualified filename required) */
        virtual bool exists(const String& filename) = 0; 

		/** Retrieve the modification time of a given file */
		virtual time_t getModifiedTime(const String& filename) = 0; 


        /** Find all files or directories matching a given pattern in this
            archive and get some detailed information about them.
        @param pattern The pattern to search for; wildcards (*) are allowed
        @param recursive Whether all paths of the archive are searched (if the 
        archive has a concept of that)
        @param dirs Set to true if you want the directories to be listed
            instead of files
        @returns A list of file information structures for all files matching 
            the criteria.
        */
        virtual FileInfoListPtr findFileInfo(const String& pattern, 
            bool recursive = true, bool dirs = false) = 0;

        /// Return the type code of this Archive
        const String& getType(void) const { return mType; }
        
    };
	/** @} */
	/** @} */

}

#endif
```

---

### Post by MadCow108 on 2011-05-05
you are on the right track
the problem is probably that the signature of the open changed to have a default parameter *readOnly* so the override of the child class does not override the correct signature anymore.

---

### Post by Jonas thomas on 2011-05-05
> **MadCow108 said:**
> you are on the right track
the problem is probably that the signature of the open changed to have a default parameter *readOnly* so the override of the child class does not override the correct signature anymore.

That was it...
Basically change...
	//DataStreamPtr open(const String &filename) const;
	DataStreamPtr open(const String &filename,bool readOnly =true) const;

Which brings me to the next error:

> /home/jonas/funguloids/src/mpakogre.cpp|88|warning: "/*" within comment|
/home/jonas/funguloids/src/oggstream.cpp||In member function ‘void OggStream::logInfo()’:|
/home/jonas/funguloids/src/oggstream.cpp|272|error: reference to ‘stringstream’ is ambiguous|
/usr/local/include/OGRE/OgrePrerequisites.h|449|error: candidates are: typedef struct Ogre::StringStream Ogre::stringstream|
/usr/include/c++/4.4/iosfwd|135|error:                 typedef struct std::basic_stringstream<char, std::char_traits<char>, std::allocator<char> > std::stringstream|
/home/jonas/funguloids/src/oggstream.cpp|272|error: reference to ‘stringstream’ is ambiguous|
/usr/local/include/OGRE/OgrePrerequisites.h|449|error: candidates are: typedef struct Ogre::StringStream Ogre::stringstream|
/usr/include/c++/4.4/iosfwd|135|error:                 typedef struct std::basic_stringstream<char, std::char_traits<char>, std::allocator<char> > std::stringstream|
/home/jonas/funguloids/src/oggstream.cpp|272|error: expected ‘;’ before ‘ss’|
/home/jonas/funguloids/src/oggstream.cpp|273|error: ‘ss’ was not declared in this scope|
||=== Build finished: 8 errors, 1 warnings (0 minutes, 38 seconds) ===|

This error... Makes sense to me..
```
void OggStream::logInfo()
{
	**//stringstream ss; Need to change to**
        Ogre::stringstream ss;   
	ss	<< "version         " << mVorbisInfo->version         << "\n"
		<< "channels        " << mVorbisInfo->channels        << "\n"
		<< "rate (hz)       " << mVorbisInfo->rate            << "\n"
		<< "bitrate upper   " << mVorbisInfo->bitrate_upper   << "\n"
		<< "bitrate nominal " << mVorbisInfo->bitrate_nominal << "\n"
		<< "bitrate lower   " << mVorbisInfo->bitrate_lower   << "\n"
		<< "bitrate window  " << mVorbisInfo->bitrate_window  << "\n"
		<< "\n"
		<< "vendor " << mVorbisComment->vendor << "\n";

	for(int i = 0; i < mVorbisComment->comments; i++)
		ss << "   " << mVorbisComment->user_comments[i] << "\n";

	LogManager::getSingleton().logMessage("OggStream::info\n" + ss.str() );
}
```


That showed up in a couple of places...

Another critter that seems to have showed up is
need to add a std:: before vector.  I added that in a bunch of places.
static std::vector<Light*> scriptLights;

Is there some kind of change in the standard that cause this?

---

### Post by slavik on 2011-05-05
only if that C++ code is very old.

---

