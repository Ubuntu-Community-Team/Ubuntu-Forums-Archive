---
title: "C++ mutlthreading synchronization issue"
date: 2013-11-01
forum: Programming Talk
---

### Post by gbgirija.here on 2013-11-01
I have an issue with my code ... my below code is createing databases(database here is a kd tree)  and indexing one image per database. i have two classes LastDatabaseTndexingPolicy  and another  forwardingDatabaseaccessor.cpp .
        
I am calling the GetDatabaseToAccess() function from forwardingDatabaseAccessor.cpp class  .GetDatabaseToAccess() function is present in LastDatabaseTndexingPolicy class and it returns the database created as a pointer and using that database pointer we call another function which actually indexes the image to the database . 
    
Now my issue is i am not able to have multiple threads act on the following functions as DatabaseAccessor_ptr db which is in the following file is coupled with two functions and however i put locks in the LastDatabaseTndexingPolicy file as below i end up getting synchronization issue ..........
        
Hence now i am using a single lock in forwardingDatabaseAccessor.cpp and serializing the code,.can anyone suggest me how can i change my design to parallelize this code .........
    
In ForwardingDatabaseAccessor.cpp we are calling function from LastDatabaseTndexingPolicy as shown below:-

DatabaseAccessor_ptr db is something which needs to be synchroinized. I tried createing 256 databases with one image each and when i run this code i ended up creating 175 databses and though i was restricting in code with locks that every database has only one image i ended up having two images in single database ..... ideally i had to get only one image per database but i got two images in few of them hence instead of 256 database this code created 175 or so databases.
      
    indexing::IndexReturnValue ForwardDatabaseAccessor::index(cv::Mat image,
    		const std::string& imageName, features::Camera::Type indexCameraType,
    		features::Camera::Type recogCameraType) {  
        DatabaseAccessor_ptr db = this->IndexingPolicy_ptr->GetDBToIndex();
        
        	return db->index(image, imageName, indexCameraType, recogCameraType);
    }
    
        
        In file LastDatabaseTndexingPolicy we have this function GetDatabaseToIndex as follows:----
        
        
        DatabaseAccessor_ptr LastDatabaseIndexingPolicy::GetDBToIndex()
         {
        	int numDBs;
        	std::string db_Name;
        	size_t totNoOfIndexedImagesInDB;
        	DatabaseAccessor_ptr db;
        	std::vector<std::string>::iterator endIter;
        	{
        		READING_LOCK(lock, adbMutex);
        		numDBs = this->associateDBs->GetNumberOfAssociateDBs();
        		endIter = this->associateDBs->end();
        		endIter--;
        		
        	}
        	if (numDBs == 0) {
        
        		std::string newDBName = this->CreateAssociateDBs(numDBs);
        		{
        			WRITING_LOCK(lock, dbMutex);
        			db = dbGroup.getDatabase(newDBName);
        			return db;
        		}
        
        	}
        
        	else {
        
        
        			WRITING_LOCK_ADV(writeLock, dbMutex);
        			totNoOfIndexedImagesInDB = dbGroup.getDatabase(*endIter)->size();
        			if (totNoOfIndexedImagesInDB >= (this->maxNumberOfImagesDBCFG))
        			{
        				writeLock.unlock();
        				std::string newDBName = this->CreateAssociateDBs(numDBs);
        				{
        				WRITING_LOCK(lock, dbMutex);
        				db = dbGroup.getDatabase(newDBName);
        				return db;
        				}
        			}
        			else
        			{
        
        				db = dbGroup.getDatabase(*endIter);
        				return db;
        				writeLock.unlock();
        
        			}
        			return db;
        		}
        	}
        
        
        
        
        
        
        std::string IndexToLastDB::CreateAssociateDBs(int numDB) {
        
        
        
        		std::ostringstream convert;
        		convert << (numDB + 1);
        		std::string newDBName = this->dbName + "_server_fwd_" + convert.str();
        		std::string db_properties = "type=ripe";
        		LOG(info,dbName) << "Name of the new database: " << newDBName;
        		{
        			WRITING_LOCK(lock, dbMutex);
        			dbGroup.createDatabase(newDBName, db_properties);
        		}
        
        		{
        			WRITING_LOCK(lock, adbMutex);
        			this->associateDBs->AddAssociateDB(newDBName);
        		}
        		{
        			WRITING_LOCK(fileLock, fileMutex);
        			util::serialization::save<indexing::forward::AssociateDBCollection>(
        					*this->associateDBs, dbFile.string(), serializationFormat);
        		}
        
        		return newDBName;
        
        	}

---

### Post by ofnuts on 2013-11-01
I see way too many locks (and even some embedded lock scopes) in there to believe that this will work properly.You can't really test multithread code. You must be able to prove that it is correct, and the more locks, the harder the proof.

If I follow you, your code behaves as if the test 
```

totNoOfIndexedImagesInDB = dbGroup.getDatabase(*endIter)->size();
if (totNoOfIndexedImagesInDB >= (this->maxNumberOfImagesDBCFG))

```

doesn't work... so what do you see when you put a printf() there (you can't really single step this kind of issues with a debugger, even a printf can already be enough to change the order of execution)...

---

