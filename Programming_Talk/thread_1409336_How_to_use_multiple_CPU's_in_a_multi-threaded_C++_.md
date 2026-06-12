---
title: "How to use multiple CPU's in a multi-threaded C++ program?"
date: 2010-02-17
forum: Programming Talk
---

### Post by T0MA on 2010-02-17
Hi all,
I have been working on a C++ code using POSIX threads. What I would like to achieve is that each thread that I have create would take advantage of the fact that the computer the code is running on has two quad-core cpu's. Ideally, each thread would be able to run on a separate CPU.

The threads have been created successfully and everything seems fine, but when I run top and hit 1 I only see one processor spinning at 100%:


top - 13:10:22 up 31 days, 19:49,  5 users,  load average: 1.65, 1.81, 1.02
Tasks: 142 total,   2 running, 140 sleeping,   0 stopped,   0 zombie
Cpu0  : 11.6%us,  7.6%sy,  0.0%ni, 65.4%id, 13.3%wa,  0.0%hi,  0.7%si,  1.3%st
Cpu1  :  0.7%us,  0.0%sy,  0.0%ni, 85.7%id, 13.6%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu2  :  0.7%us,  0.3%sy,  0.0%ni, 98.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.3%st
Cpu3  :  0.3%us,  0.0%sy,  0.0%ni, 85.0%id, 14.7%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu4  :  0.7%us,  1.0%sy,  0.0%ni, 98.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu5  :  0.7%us,  1.3%sy,  0.0%ni, 97.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.3%st
Cpu6  :  0.7%us,  0.3%sy,  0.0%ni, 99.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu7  : 42.0%us, 58.0%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   8117192k total,  7027000k used,  1090192k free,    64940k buffers
Swap:  2957304k total,    94476k used,  2862828k free,  3050800k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND          
 5786 becat     20   0 2941m 2.7g 2392 R  144 35.4  10:59.22 feature_extract  


The code is feature_extract and it has 5 threads that run simultaneously. Each thread had been initialized with the attribute THREAD_SCOPE_SYSTEM:
```

pthread_attr_init (&(ql->readerAttr[z]));
pthread_attr_setscope(&(ql->readerAttr[z]), THREAD_SCOPE_SYSTEM);
pthread_create(&(ql->readerThreads[z]), &(ql->readerAttr[z]), &QueueManager::queueReader, (void *)ql->queueList[z]);

```

_What am I missing?_


Just in case, here is the code that is responsible for setting up the threads:

```

/*
 * QueueManager
 *
 * Creates POSIX threads to handle the capture
 * and analyzes of the network traffic
 * 
 * 2009-2010
 *
 * University of Connecticut
 */

#include "QueueManager.h"

using namespace std;

QueueManager::QueueManager() {}
QueueManager::~QueueManager() {}

int main(int argc, char *argv[]) {
	/*
	 * Check for the correct number of input parameteres
	 */
	if(argc<2) {
		cout << "usage: %s <network device or pcap file> [seconds of capture]\n ";
		cout << "example: %s capture_2008_09_03_filtered.pcap\n";
		cout << "if [seconds of capture] is not specified, its an offline capture";
		return 1;
	}

	cout << "Extracting Network Features" << "\n";

	int numberOfProcessors=4;

	time_t timeElapsed=0, startTime=time(NULL), difference=0;
	//initscr();
	int row,col;
	getmaxyx(stdscr,row,col);
	//mvprintw(row/2-6,(col-27)/2,"%s","Feature extraction started.");
	mvprintw(row-2,(col-80)/2,"University of Connecticut (c) C++ Feature Extractor | Tamas K Lengyel 2009-2010");
	mvprintw(row-1,(col-75)/2,"");
	refresh();

	structures::queueList *ql;
	ql=(structures::queueList*)malloc(sizeof(structures::queueList));
	ql->timeOut=(time_t)1; // Set timeout
	ql->pcapFile=argv[1];
	ql->numberOfQueues=numberOfProcessors;

	for(int z=0; z<numberOfProcessors; z++) {
		ql->queueList[z]=(structures::queue*)malloc(sizeof(structures::queue));
		structures::queue* pq;
		pq=ql->queueList[z];
		structures::queueNode *start;
		start=(structures::queueNode*)malloc(sizeof(structures::queueNode));
		start->stage=0;
		pq->start=start;
		pq->empty=true;
		pq->conn=new mysqlpp::Connection("flows", "127.0.0.1", "becat", "xxxxx", 3306);
		pq->builderDone=false;
	}


	ql->packets=pcap_open_offline(ql->pcapFile, ql->pcapErr);
	if(ql->packets==NULL) {
		std::cout << "Failed to open \""<<ql->pcapFile<<"\"! Error: "<< ql->pcapErr << "\n";
		return 0;
	} else {

		pthread_attr_init (&(ql->builderAttr));
		pthread_attr_setscope(&(ql->builderAttr), PTHREAD_SCOPE_SYSTEM);

		pthread_create(&(ql->builder), &(ql->builderAttr), &QueueManager::queueBuilder, (void *)ql);

		for(int z=0; z<numberOfProcessors; z++) {
			pthread_attr_init (&(ql->readerAttr[z]));
			pthread_attr_setscope(&(ql->readerAttr[z]), PTHREAD_SCOPE_SYSTEM);
			pthread_create(&(ql->readerThreads[z]), &(ql->readerAttr[z]), &QueueManager::queueReader, (void *)ql->queueList[z]);
		}


		//int totalProcessed=0;

		/*pthread_join(ql->builder,NULL);

		std::cout << "Finished receiving packets\n";

		for(int z=0; z<numberOfProcessors; z++) {
			pthread_join(ql->readerThreads[z],NULL);
			std::cout << "Thread " << z << "finished\n";
		}*/


		while(pthread_tryjoin_np(ql->builder,NULL)) {
			difference=time(NULL)-startTime;
			if(difference!=timeElapsed) {
				timeElapsed=difference;

				//std::cout << time(NULL) << ": Packets are coming in.\n";

				//mvprintw(0,0, "%s %f %s", "INCOMING: ", ql->speed, "Mbit/s            ");
				//mvprintw(1,0,"%s %d", "Packet count: ", ql->packetCount);
				//mvprintw(2,0, "%s %f %s", "Average speed: ", ql->speedAverage, "Mbit/s                  ");
				//int v;
				//for(v=0;v<numberOfProcessors;v++) {

				//totalProcessed+=ql->queueList[v]->packetCount;

				//mvprintw(v*3+3,0, "%s %d%s %f %s %f %s", "PROCESSING THREAD", v, ": ", ql->queueList[v]->speed, "Mbit/s; Average speed: ", ql->queueList[v]->speedAverage, "                ");
				//mvprintw(v*3+4,0, "%s %d", "Packet count: ", ql->queueList[v]->packetCount);
				//mvprintw(v*3+5,0, "%s %d %s %d %s", "Detected flows: ", ql->queueList[v]->totalFlows, "; Finished flows: ", ql->queueList[v]->finishedFlows, "           ");

			}

			//mvprintw(row-5,0, "%s %d %s", "Total number of packets processed:   ", totalProcessed, "        ");
			//mvprintw(row-4,0, "%s %d %s", "Total number of packets unprocessed: ", ql->packetCount-totalProcessed, "          ");
			//refresh();

			//std::cout << "Processed: " << totalProcessed << "\n";
			//std::cout << "Unprocessed: "<< ql->packetCount-totalProcessed << "\n";

			//totalProcessed=0;
			//}
		}

		for(int z=0; z<numberOfProcessors; z++) {
			while(pthread_tryjoin_np(ql->readerThreads[z],NULL)) {
				difference=time(NULL)-startTime;
				if(difference!=timeElapsed) {
					timeElapsed=difference;
					//std::cout << time(NULL) << ": thread " << z << " is working.\n";
					//mvprintw(0,0, "%s %f %s", "INCOMING: ", ql->speed, "Mbit/s            ");
					//mvprintw(1,0,"%s %d", "Packet count: ", ql->packetCount);
					//mvprintw(2,0, "%s %f %s", "Average speed: ", ql->speedAverage, "Mbit/s                  ");
					//int v;
					//for(v=0;v<numberOfProcessors;v++) {

					//totalProcessed+=ql->queueList[v]->packetCount;

					//mvprintw(v*3+3,0, "%s %d%s %f %s %f %s", "PROCESSING THREAD", v, ": ", ql->queueList[v]->speed, "Mbit/s; Average speed: ", ql->queueList[v]->speedAverage, "                ");
					//mvprintw(v*3+4,0, "%s %d", "Packet count: ", ql->queueList[v]->packetCount);
					//mvprintw(v*3+5,0, "%s %d %s %d %s", "Detected flows: ", ql->queueList[v]->totalFlows, "; Finished flows: ", ql->queueList[v]->finishedFlows, "           ");

					//}

					//mvprintw(row-5,0, "%s %d %s", "Total number of packets processed:   ", totalProcessed, "        ");
					//mvprintw(row-4,0, "%s %d %s", "Total number of packets unprocessed: ", ql->packetCount-totalProcessed, "          ");
					//refresh();

					//totalProcessed=0;
				}
			}
		}

		//mvprintw((row/2)-5,(col-26)/2, "%s", "FEATURE EXTRACTOR FINISHED");
		//refresh();
		//endwin();


		std::cout << "Finished processing " << ql->packetCount << " packets.\n";
		std::cout << "Average build speed: \t" << ql->speedAverage << " Mbit/s \tPacket speed: \t" << ql->packetSpeedAverage<< " packets/s\n";
		//std::cout << "Average processing speed: \t" << pq->readSpeedAverage << " Mbit/s \tPacket speed: \t"<< pq->readPacketSpeedAverage<< " packets/s\n";
		//std::cout << "Detected number of flows: \t" << pq->totalFlows << "\n";
		//std::cout << "Detected flow time-outs: \t" << pq->finishedFlows << "\n";

		return 0;
	}

	return 1;
}

void* QueueManager::queueBuilder(void *input) {

	structures::queueList *ql = (structures::queueList *)input;
	pcap_t *packets=ql->packets;

	cout << "Builder is " << pthread_self() << "\n";

	if(packets==NULL) {
		std::cout << "Failed to open \""<<ql->pcapFile<<"\"! Error: "<< ql->pcapErr << "\n";
		pthread_exit(0);
	} else {
		const u_char *packet;        /* The actual packet */
		struct pcap_pkthdr hdr;      /* The header that pcap gives us */
		bool loop=true;				 /* Determines if the loop should continue */
		time_t timeOut=time(NULL)+ql->timeOut;
		time_t timeElapsed=0, startTime=time(NULL), difference=0;
		double speed=0, speedSum=0, speedAverage=0;
		double packetSpeed=0, packetSpeedSum=0,packetSpeedAverage=0;
		int count=0;
		FeatureExtractor extractor;

		for(packet=pcap_next(packets, &hdr);loop;count++) {
			while(packet==NULL && timeOut<=time(NULL)) {
				packet=pcap_next(packets,&hdr);
			}

			if(packet==NULL) {
				pcap_close(packets);
				break;
			} else {

				timeOut=time(NULL)+1;
				structures::queueNode *newNode;
				newNode=(structures::queueNode*)malloc(sizeof(structures::queueNode));

				newNode->packetFeatures=extractor.extractBasicFeatures(packet, hdr);
				newNode->stage=1;

				if(newNode->packetFeatures.packetTime != NULL) {
					int queueNumber = newNode->packetFeatures.sourceIP.byte4 % ql->numberOfQueues;

					if(ql->queueList[queueNumber]->empty) {
						ql->queueList[queueNumber]->start->prev=NULL;
						ql->queueList[queueNumber]->start->next=NULL;
						ql->queueList[queueNumber]->start=newNode;
						ql->queueList[queueNumber]->end=ql->queueList[queueNumber]->start;
						ql->queueList[queueNumber]->empty=false;
					} else {
						newNode->prev=ql->queueList[queueNumber]->end;
						ql->queueList[queueNumber]->end=newNode;
						ql->queueList[queueNumber]->end->prev->next=newNode;
					}
				}

				//extractor.handlePacket(pq->end->packetFeatures);

				difference=time(NULL)-startTime;
				speed+=(double)hdr.len;
				packetSpeed+=1;
				if(difference!=timeElapsed) {
					timeElapsed=difference;
					speed/=131072; // Convert to Mbit
					speedSum+=speed;
					speedAverage=speedSum/timeElapsed;
					packetSpeedSum+=packetSpeed;
					packetSpeedAverage=packetSpeedSum/timeElapsed;

					ql->speed=speed;
					ql->packetCount=count;
					ql->speedAverage=speedAverage;
					ql->packetSpeed=packetSpeed;
					ql->packetSpeedAverage=packetSpeedAverage;

					speed=0;
					packetSpeed=0;

					//std::cout << "Builder still working! "<< packetSpeedAverage <<"\n";
				}

				//GRAB NEXT PACKET
				packet=pcap_next(packets, &hdr);
			}
		}

		speed/=131072;
		speedSum+=speed;
		speedAverage=speedSum/timeElapsed;
		packetSpeedSum+=packetSpeed;
		packetSpeedAverage=packetSpeedSum/timeElapsed;
		ql->speed=speed;
		ql->packetCount=count;
		ql->speedAverage=speedAverage;
		ql->packetSpeed=packetSpeed;
		ql->packetSpeedAverage=packetSpeedAverage;

		for(int z=0; z<ql->numberOfQueues; z++) {
			ql->queueList[z]->builderDone=true;
		}

		cout << "Builder done. Count: "<< count << "\n";

		pthread_exit(0);
	}
}

void* QueueManager::queueReader(void *input) {

	cout << "A reader is " << pthread_self() << "\n";

	structures::queue *pq = (structures::queue *)input;
	FeatureExtractor extractor;
	time_t lastHousekeeping=time(NULL);
	time_t timeElapsed=0, startTime=time(NULL), difference=0;
	double speed=0, speedSum=0, speedAverage=0;
	double packetSpeed=0, packetSpeedSum=0,packetSpeedAverage=0;
	int count=0;

	if(!pq->conn->connect("flows", "127.0.0.1", "becat", "xxxxx", 3306)) {
		std::cout << "DB connection failed: " << pq->conn->error() << "\n";
	}

	bool loop=true;

	while(loop) {
		if(pq->start!=pq->end) {
			if(pq->start!=NULL && pq->start->stage==1) {


				extractor.handlePacket(pq->start->packetFeatures, pq->conn);

				pq->totalFlows=extractor.basicFeatures.flowCounter;
				pq->finishedFlows=extractor.basicFeatures.finishedFlowCounter;
				pq->start->stage=2;

				count++;
				difference=time(NULL)-startTime;
				speed+=(double)pq->start->packetFeatures.packetSize;
				packetSpeed+=1;
				if(difference!=timeElapsed) {
					timeElapsed=difference;
					speed/=131072; // Convert to Mbit
					speedSum+=speed;
					speedAverage=speedSum/timeElapsed;
					packetSpeedSum+=packetSpeed;
					packetSpeedAverage=packetSpeedSum/timeElapsed;

					pq->speed=speed;
					pq->packetCount=count;
					pq->speedAverage=speedAverage;
					pq->packetSpeed=packetSpeed;
					pq->packetSpeedAverage=packetSpeedAverage;

					speed=0;
					packetSpeed=0;
					//cout << pthread_self() << ": " << count << "\n";
				}

			}

			if(pq->start!=NULL && pq->start->next!=NULL) {
				delete(pq->start->prev);
				pq->start=pq->start->next;
			}
		} else {
			cout << time(NULL) << ":" << pthread_self() << " Reader at end of the list, lets sleep!\n";
			sleep(1);
			if(pq->start==pq->end && pq->builderDone) {
				loop=false;
				cout << time(NULL) << ":" << pthread_self() << "Reader is exiting loop!\n";
			}
		}

		if( (time(NULL)-lastHousekeeping>120) && (!pq->builderDone) ) {
			//pq->houseKeepingRunning=true;
			//extractor.houseKeepingStart();
			extractor.flows=extractor.houseKeeping(extractor.flows,1);
			//extractor.houseKeepingDone();
			lastHousekeeping=time(NULL);
			//pq->houseKeepingRunning=false;
		}
	}

	extractor.handlePacket(pq->end->packetFeatures, pq->conn);
	//pq->houseKeepingRunning=true;
	extractor.houseKeeping(extractor.flows,1);
	//pq->houseKeepingRunning=false;

	pq->totalFlows=extractor.basicFeatures.flowCounter;
	pq->finishedFlows=extractor.basicFeatures.finishedFlowCounter;

	speed/=131072;
	speedSum+=speed;
	speedAverage=speedSum/timeElapsed;
	packetSpeedSum+=packetSpeed;
	packetSpeedAverage=packetSpeedSum/timeElapsed;
	pq->speed=speed;
	pq->packetCount=count+1;
	pq->speedAverage=speedAverage;
	pq->packetSpeed=packetSpeed;
	pq->packetSpeedAverage=packetSpeedAverage;

	std::cout << "Reading is done\n";

	pthread_exit(0);
}


```

---

