---
title: "Init Gtk on demand from another thread"
date: 2013-01-08
forum: Programming Talk
---

### Post by bird1500 on 2013-01-08
Hi,
It's a file I/O app that only shows the GUI if a few seconds passed and it's not done yet.
From main() I start one or more I/O threads (tasks) and any of them might require to init Gtk and create the (single) gtk window at any time.
The trick is to only init Gtk and create a window once, and only when requested by a thread, not in advance, and do it asap.

My prototype does it with pthreads, is there a pure Gtk/glib way to do it?
I looked at Glib's main loop/context and couldn't figure out.

[PHP]
#include <gtkmm.h>
#include <pthread.h>
#include <stdint.h>

#define ThreadInfo() printf("THREAD_ID %llX: {%d}{%s}\n", \
(long long unsigned)pthread_self(), __LINE__, __FUNCTION__)

#define L printf("PING {%d}{%s}\n", __LINE__, __FUNCTION__ )

void* aThread(void*);
bool initGtkAndShowWindow();

struct launch_gtk_t {
    pthread_mutex_t mutex;
    pthread_cond_t cond;
    bool doLaunch;
};

launch_gtk_t launchGtk = {
    PTHREAD_MUTEX_INITIALIZER, PTHREAD_COND_INITIALIZER, false
};

int main(int argc, char *argv[]) {
    
    ThreadInfo();
    pthread_t thread;
    
    for(int i=0; i<5; i++) {
        pthread_create(&thread, NULL, aThread, NULL);
    }
    
    while(!launchGtk.doLaunch) {
        int status = pthread_mutex_lock(&launchGtk.mutex);
        if(status != 0) {
            perror("mutex lock");
            break;
        }
        
        status = pthread_cond_wait(&launchGtk.cond, &launchGtk.mutex);
        if(status != 0) {
            perror("cond wait");
            break;
        }
        
        status = pthread_mutex_unlock(&launchGtk.mutex);
        if(status != 0) {
            perror("mutex unlock");
            break;
        }
    }
    
    initGtkAndShowWindow();
L;
    return 0;
}

bool
initGtkAndShowWindow() {
    ThreadInfo();
    Gtk::Main kit(true);
    
    Gtk::Window win;
    win.set_size_request(600, 200);
    win.show_all();
    kit.run(win);
    return false;
}

void*
aThread(void*) {
    pthread_detach(pthread_self());
    ThreadInfo();
    
    int status = pthread_mutex_lock(&launchGtk.mutex);
    if(status != 0) {
        perror("lock mutex");
        return NULL;
    }
    
    if(!launchGtk.doLaunch) {
        launchGtk.doLaunch = true;
        
        status = pthread_cond_signal(&launchGtk.cond);
        if(status != 0) {
            perror("cond signal");
            return NULL;
        }
    }
    
    status = pthread_mutex_unlock(&launchGtk.mutex);
    if(status != 0) {
        perror("mutex unlock");
    }
L;
    return NULL;
}

[/PHP]

---

