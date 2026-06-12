---
title: "python 3 tkinter not showing print function"
date: 2017-04-05
forum: Programming Talk
---

### Post by lance bermudez on 2017-04-05
I'm trying to learn tkinter my whole scripts is 
```

import tkinter
import tkinter.messagebox
import zipfile               # zipfile for python 3.4 zipapp for python 3.5
from os.path import join     # os.path.join
from os.path import isdir    # os.path.isdir
from os.path import isfile   # os.path.isfile
from os.path import splitext # os.path.splitext
from os import getenv        # os.getenv
from os import listdir       # os.listdir
from os import chdir         # os.chdir
from os import remove        # os.remove
from os import getcwd        # os.getcwd
from os import makedirs
from os import walk
import gnupg                 # gnupg
from shutil import rmtree    # shutil.rmtree
from shutil import move      # shutil.move

def c_files(source_dir):
    for filename in listdir(source_dir): # for loop to display filename in list column
        if not filename.endswith('.zip'):
            yield filename

def lsDir(parent):
    return [d for d in listdir(parent) if isdir(join(parent, d))]

def zipdir(source_dir, ziph):
    for root, dirs, files in walk(source_dir, topdown=True):
        for file in files:
            ziph.write(join(root, file))

def Mk_LAZMA_Zip_Files(source_dir, dest_dir):
    #print('This will zip all the files in the\n', source_dir)
    #print('\n')
    #print('It will place the ziped files in the\n', dest_dir)
    #print('\n')
    
    chdir(source_dir)

    # mk Directory zip files for Deflated
    for csv_filename in lsDir(source_dir):        
        file_root = splitext(csv_filename)[0] # will give the file not file.txt
        zip_file_name = file_root + '_DIRECTORY_ZIP_LZMA.zip' # will let you add .zip to file for file.zip
        zip_file_path = join(dest_dir, zip_file_name) # will put new file in dest_dir
        print('Zipping Directory', csv_filename)
        #tkinter.messagebox.showinfo('Zipping Directory', csv_filename)
        main_window = tkinter.Tk()
        value = tkinter.StringVar()
        label = tkinter.Label(main_window,
                              text=csv_filename)
        label.pack()
        tkinter.mainloop()
        
        #print('Using LAZMA Compression')
        #print('')
        zipf = zipfile.ZipFile(zip_file_path, 'w', compression=zipfile.ZIP_LZMA,
                             allowZip64=True)
        zipdir(csv_filename, zipf)
        zipf.close()
        if isdir(csv_filename): # find any dir in source
            print('Deleting directory', csv_filename)
            print('')
            rmtree(csv_filename) # remove any dir in source
            print('')

    for c_filename in c_files(source_dir):        
        file_root = splitext(c_filename)[0] # will give the file not file.txt
        zip_file_name = file_root + '_ZIP_LZMA.zip' # will let you add .zip to file for file.zip
        zip_file_path = join(dest_dir, zip_file_name) # will put new file in dest_dir
        print('Zipping File', c_filename)
        # Mk Zipfiles
        with zipfile.ZipFile(zip_file_path, mode='w',
                             compression=zipfile.ZIP_LZMA,
                             allowZip64=True) as zf:
            zf.write(c_filename)
        print('Deleting files', c_filename)
        print('')
        remove(c_filename) # remove file from source

class MyGUI:
    def __init__(self):
        # Create the main window
        self.main_window = tkinter.Tk()

        # Create a Button widget. The text 'Make folders for this script to work'
        # Should appear on the face of the Button. The
        # do_something method should be executed when
        # the user clicks the Button.
        self.my_button = tkinter.Button(self.main_window,
                                        text='Make folders for this script to work',
                                        command=self.do_something)

        # Create a Button widget. The text 'Zip files and folders'
        self.my_zip = tkinter.Button(self.main_window,
                                        text='Zip files and folders',
                                        command=self.do_zip)

        # Create a Quit Button. When this button is clicked
        # the root widget's destroy method is called.
        # (The main_windows variable references the root widget,
        # So the callback function is self.main_window.destroy.)
        self.quit_button = tkinter.Button(self.main_window,
                                          text='Quit',
                                          command=self.main_window.destroy)

        # Pack the Buttons
        self.my_button.pack()
        self.my_zip.pack()
        self.quit_button.pack()

        # Enter the tkinter main loop.
        tkinter.mainloop()

    # The do_something method is a callback function
    # For the Button widget.

    def do_something(self):
        # Make Zip Files dir
        # getting dir GPG_Files
        # ~/Documents/GPG_Files1
        chdir(join(getenv('HOME'), 'Documents'))
        b=getcwd() # get pwd
        fname = 'GPG_Files1'
        path = (b+'/'+fname)
        makedirs(path, exist_ok=True) # Check for Data_files folder mk if not

        # getting dir Files_to_GPG
        # ~/Documents/GPG_Files1/Files_to_GPG
        chdir(join(getenv('HOME'), 'Documents/GPG_Files1'))
        p=getcwd() # get pwd
        fname = 'Files_to_GPG'
        path = (p+'/'+fname)
        makedirs(path, exist_ok=True) # Check for Data_files folder mk if not

        # getting dir GPG_Files\Files_to_GPG_UPLoad
        # ~/Documents/GPG_Files1/Files_to_GPG_UPLoad
        fname = 'Files_to_GPG_UPLoad'
        path = (p+'/'+fname)
        makedirs(path, exist_ok=True)

        # ~/Documents/Data_Files1
        chdir(join(getenv('HOME'),'Documents')) # change user home dir
        b = getcwd() # get pwd
        fname = 'Data_Files1'
        path = (b+'/'+fname)
        makedirs(path, exist_ok=True)
        
        # Display an info dialog box.
        tkinter.messagebox.showinfo('Resonse',
                                    'Dir created to use script.')

    def do_zip(self):
        # Make Zip Files in dir
        # ~/Documents/GPG_Files1
        # Set Source and Destion Directories
        source_dir = join(getenv('HOME'), 'Documents/GPG_Files1/Files_to_GPG')
        dest_dir = join(getenv('HOME'), 'Documents/GPG_Files1/Files_to_GPG')
        Mk_LAZMA_Zip_Files(source_dir, dest_dir) # make zip
        
        # Display an info dialog box.
        tkinter.messagebox.showinfo('Resonse',
                                    'Ziped files and folders in ~/Documents/GPG_Files1/Files_to_GPG.')

# Create an instance of the MyGui class.
my_gui = MyGUI()

```

the part of the code i want to fix is 
```

def Mk_LAZMA_Zip_Files(source_dir, dest_dir):
    #print('This will zip all the files in the\n', source_dir)
    #print('\n')
    #print('It will place the ziped files in the\n', dest_dir)
    #print('\n')
    
    chdir(source_dir)

    # mk Directory zip files for Deflated
    for csv_filename in lsDir(source_dir):        
        file_root = splitext(csv_filename)[0] # will give the file not file.txt
        zip_file_name = file_root + '_DIRECTORY_ZIP_LZMA.zip' # will let you add .zip to file for file.zip
        zip_file_path = join(dest_dir, zip_file_name) # will put new file in dest_dir
        print('Zipping Directory', csv_filename)
        tkinter.messagebox.showinfo('Zipping Directory', csv_filename)
        #print('Using LAZMA Compression')
        #print('')
        zipf = zipfile.ZipFile(zip_file_path, 'w', compression=zipfile.ZIP_LZMA,
                             allowZip64=True)
        zipdir(csv_filename, zipf)
        zipf.close()
        if isdir(csv_filename): # find any dir in source
            print('Deleting directory', csv_filename)
            print('')
            rmtree(csv_filename) # remove any dir in source
            print('')

    for c_filename in c_files(source_dir):        
        file_root = splitext(c_filename)[0] # will give the file not file.txt
        zip_file_name = file_root + '_ZIP_LZMA.zip' # will let you add .zip to file for file.zip
        zip_file_path = join(dest_dir, zip_file_name) # will put new file in dest_dir
        print('Zipping File', c_filename)
        # Mk Zipfiles
        with zipfile.ZipFile(zip_file_path, mode='w',
                             compression=zipfile.ZIP_LZMA,
                             allowZip64=True) as zf:
            zf.write(c_filename)
        print('Deleting files', c_filename)
        print('')
        remove(c_filename) # remove file from source

```

I want the tkinter.messagebox.showinfo('Zipping Directory', csv_filename) to work without having to keep clicking the ok I want it so show the printing tags like from the cli

---

### Post by lance bermudez on 2017-04-06
New code for frames 
```

import tkinter
import tkinter.messagebox
#import tkinter.Text
from tkinter import Text
import zipfile               # zipfile for python 3.4 zipapp for python 3.5
from os.path import join     # os.path.join
from os.path import isdir    # os.path.isdir
from os.path import isfile   # os.path.isfile
from os.path import splitext # os.path.splitext
from os import getenv        # os.getenv
from os import listdir       # os.listdir
from os import chdir         # os.chdir
from os import remove        # os.remove
from os import getcwd        # os.getcwd
from os import makedirs
from os import walk
import gnupg                 # gnupg
from shutil import rmtree    # shutil.rmtree
from shutil import move      # shutil.move

def c_files(source_dir):
    for filename in listdir(source_dir): # for loop to display filename in list column
        if not filename.endswith('.zip'):
            yield filename

def lsDir(parent):
    return [d for d in listdir(parent) if isdir(join(parent, d))]

def zipdir(source_dir, ziph):
    for root, dirs, files in walk(source_dir, topdown=True):
        for file in files:
            ziph.write(join(root, file))

def Mk_LAZMA_Zip_Files(source_dir, dest_dir):
    #print('This will zip all the files in the\n', source_dir)
    #print('\n')
    #print('It will place the ziped files in the\n', dest_dir)
    #print('\n')
    
    chdir(source_dir)

    # mk Directory zip files for Deflated
    for csv_filename in lsDir(source_dir):        
        file_root = splitext(csv_filename)[0] # will give the file not file.txt
        zip_file_name = file_root + '_DIRECTORY_ZIP_LZMA.zip' # will let you add .zip to file for file.zip
        zip_file_path = join(dest_dir, zip_file_name) # will put new file in dest_dir
        print('Zipping Directory', csv_filename)
        #tkinter.messagebox.showinfo('Zipping Directory', csv_filename)
        #main_window = tkinter.Tk()
        #value = tkinter.StringVar()
        #label = tkinter.Label(main_window,
        #                      text=csv_filename)
        #label.pack()
        #tkinter.mainloop()
        #T = Text(main_window, width=67, height=10).grid()
        #T.pack()
        #T.insert(END, csv_filename)
        #main_window.mainloop()
        tkinter.Text.showinfo('Zipping Directory', csv_filename)
        
        #print('Using LAZMA Compression')
        #print('')
        zipf = zipfile.ZipFile(zip_file_path, 'w', compression=zipfile.ZIP_LZMA,
                             allowZip64=True)
        zipdir(csv_filename, zipf)
        zipf.close()
        if isdir(csv_filename): # find any dir in source
            print('Deleting directory', csv_filename)
            print('')
            rmtree(csv_filename) # remove any dir in source
            print('')

    for c_filename in c_files(source_dir):        
        file_root = splitext(c_filename)[0] # will give the file not file.txt
        zip_file_name = file_root + '_ZIP_LZMA.zip' # will let you add .zip to file for file.zip
        zip_file_path = join(dest_dir, zip_file_name) # will put new file in dest_dir
        print('Zipping File', c_filename)
        # Mk Zipfiles
        with zipfile.ZipFile(zip_file_path, mode='w',
                             compression=zipfile.ZIP_LZMA,
                             allowZip64=True) as zf:
            zf.write(c_filename)
        print('Deleting files', c_filename)
        print('')
        remove(c_filename) # remove file from source

class MyGUI:
    def __init__(self):
        # Create the main window
        self.main_window = tkinter.Tk()

        # creat 3 frames top, middle, bottom
        self.top_frame = tkinter.Frame(self.main_window)
        self.bottom_frame = tkinter.Frame(self.main_window)

        # Create a Button widget. The text 'Make folders for this script to work'
        # Should appear on the face of the Button. The
        # do_something method should be executed when
        # the user clicks the Button.
        self.my_button = tkinter.Button(self.top_frame,
                                        text='Make folders for this script to work',
                                        command=self.do_something)

        # Create a Button widget. The text 'Zip files and folders'
        self.my_zip = tkinter.Button(self.top_frame,
                                        text='Zip files and folders',
                                        command=self.do_zip)

        # Create a Quit Button. When this button is clicked
        # the root widget's destroy method is called.
        # (The main_windows variable references the root widget,
        # So the callback function is self.main_window.destroy.)
        self.quit_button = tkinter.Button(self.top_frame,
                                          text='Quit',
                                          command=self.main_window.destroy)

        # Pack the Buttons
        self.my_button.pack(side='top')
        self.my_zip.pack(side='top')
        self.quit_button.pack(side='right')

        # StringVar object to associate with output label
        self.value1 = tkinter.StringVar()
        self.value2 = tkinter.StringVar()

        # label associate with StringVar
        self.descr_lable = tkinter.Label(self.bottom_frame,
                                   textvariable=self.value1)
        self.miles_lable = tkinter.Label(self.bottom_frame,
                                   textvariable=self.value2)
        self.descr_lable.pack(side='left')
        self.miles_lable.pack(side='left')
        
        # Pack the Frames
        self.top_frame.pack()
        self.bottom_frame.pack()
        
        # Enter the tkinter main loop.
        tkinter.mainloop()

    # The do_something method is a callback function
    # For the Button widget.

    def do_something(self):
        # Make Zip Files dir
        # getting dir GPG_Files
        # ~/Documents/GPG_Files1
        #miles1="checking for ~/Documents/GPG_Files1 and if you dont exit it mill make\n"
        self.value.set('''checking for\n ~/Documents/GPG_Files2\n ~/Documents/GPG_Files2/Files_to_GPG\n ~/Documents/GPG_Files2/Files_to_GPG_UPLoad\n if the dont exit it mill make them''')
        chdir(join(getenv('HOME'), 'Documents'))
        b=getcwd() # get pwd
        fname = 'GPG_Files2'
        path = (b+'/'+fname)
        makedirs(path, exist_ok=True) # Check for Data_files folder mk if not

        # getting dir Files_to_GPG
        # ~/Documents/GPG_Files1/Files_to_GPG
        chdir(join(getenv('HOME'), 'Documents/GPG_Files2'))
        p=getcwd() # get pwd
        fname = 'Files_to_GPG'
        path = (p+'/'+fname)
        makedirs(path, exist_ok=True) # Check for Data_files folder mk if not

        # getting dir GPG_Files\Files_to_GPG_UPLoad
        # ~/Documents/GPG_Files1/Files_to_GPG_UPLoad
        fname = 'Files_to_GPG_UPLoad'
        path = (p+'/'+fname)
        makedirs(path, exist_ok=True)

        # ~/Documents/Data_Files1
        chdir(join(getenv('HOME'),'Documents')) # change user home dir
        b = getcwd() # get pwd
        fname = 'Data_Files2'
        path = (b+'/'+fname)
        makedirs(path, exist_ok=True)
        
        # Display an info dialog box.
        #tkinter.messagebox.showinfo('Resonse',
                                    #'Dir created to use script.')
        # update StringVar
        # this will automatically update the miles_label widget
        #miles = "Dir created to use script."
        #self.value.set(miles)

    def do_zip(self):
        # Make Zip Files in dir
        # ~/Documents/GPG_Files1
        # Set Source and Destion Directories
        source_dir = join(getenv('HOME'), 'Documents/GPG_Files1/Files_to_GPG')
        dest_dir = join(getenv('HOME'), 'Documents/GPG_Files1/Files_to_GPG')
        #Mk_LAZMA_Zip_Files(source_dir, dest_dir) # make zip
        chdir(source_dir)
        for csv_filename in lsDir(source_dir):
            file_root = splitext(csv_filename)[0] # will give the file not file.txt
            zip_file_name = file_root + '_DIRECTORY_ZIP_LZMA.zip' # will let you add .zip to file for file.zip
            zip_file_path = join(dest_dir, zip_file_name) # will put new file in dest_dir
            self.value1.set('Zipping Directory ')
            self.value2.set(csv_filename)
            #print('Zipping Directory', csv_filename)
            zipf = zipfile.ZipFile(zip_file_path, 'w', compression=zipfile.ZIP_LZMA,
                                   allowZip64=True)
            zipdir(csv_filename, zipf)
            zipf.close()
            if isdir(csv_filename): # find any dir in source
                self.value1.set('Deleting directory ')
                self.value2.set(csv_filename)
                #print('Deleting directory', csv_filename)
                #print('')
                rmtree(csv_filename) # remove any dir in source
                #print('')
        for c_filename in c_files(source_dir):
            file_root = splitext(c_filename)[0] # will give the file not file.txt
            zip_file_name = file_root + '_ZIP_LZMA.zip' # will let you add .zip to file for file.zip
            zip_file_path = join(dest_dir, zip_file_name) # will put new file in dest_dir
            self.value1.set('Zipping File ')
            self.value2.set(c_filename)
            #print('Zipping File', c_filename)
            # Mk Zipfiles
            with zipfile.ZipFile(zip_file_path, mode='w',
                                 compression=zipfile.ZIP_LZMA,
                                 allowZip64=True) as zf:
                zf.write(c_filename)
            self.value1.set('Deleting files ')
            self.value2.set(c_filename)
            #print('Deleting files', c_filename)
            #print('')
            remove(c_filename) # remove file from source
        
        # Display an info dialog box.
        #tkinter.messagebox.showinfo('Resonse',
                                    #'Ziped files and folders in ~/Documents/GPG_Files1/Files_to_GPG.')

# Create an instance of the MyGui class.
my_gui = MyGUI()

```

the code i changed now shows nothing tell it gets done running no output as it is running
```

def do_zip(self):
        # Make Zip Files in dir
        # ~/Documents/GPG_Files1
        # Set Source and Destion Directories
        source_dir = join(getenv('HOME'), 'Documents/GPG_Files1/Files_to_GPG')
        dest_dir = join(getenv('HOME'), 'Documents/GPG_Files1/Files_to_GPG')
        #Mk_LAZMA_Zip_Files(source_dir, dest_dir) # make zip
        chdir(source_dir)
        for csv_filename in lsDir(source_dir):
            file_root = splitext(csv_filename)[0] # will give the file not file.txt
            zip_file_name = file_root + '_DIRECTORY_ZIP_LZMA.zip' # will let you add .zip to file for file.zip
            zip_file_path = join(dest_dir, zip_file_name) # will put new file in dest_dir
            self.value1.set('Zipping Directory ')
            self.value2.set(csv_filename)
            #print('Zipping Directory', csv_filename)
            zipf = zipfile.ZipFile(zip_file_path, 'w', compression=zipfile.ZIP_LZMA,
                                   allowZip64=True)
            zipdir(csv_filename, zipf)
            zipf.close()
            if isdir(csv_filename): # find any dir in source
                self.value1.set('Deleting directory ')
                self.value2.set(csv_filename)
                #print('Deleting directory', csv_filename)
                #print('')
                rmtree(csv_filename) # remove any dir in source
                #print('')
        for c_filename in c_files(source_dir):
            file_root = splitext(c_filename)[0] # will give the file not file.txt
            zip_file_name = file_root + '_ZIP_LZMA.zip' # will let you add .zip to file for file.zip
            zip_file_path = join(dest_dir, zip_file_name) # will put new file in dest_dir
            self.value1.set('Zipping File ')
            self.value2.set(c_filename)
            #print('Zipping File', c_filename)
            # Mk Zipfiles
            with zipfile.ZipFile(zip_file_path, mode='w',
                                 compression=zipfile.ZIP_LZMA,
                                 allowZip64=True) as zf:
                zf.write(c_filename)
            self.value1.set('Deleting files ')
            self.value2.set(c_filename)
            #print('Deleting files', c_filename)
            #print('')
            remove(c_filename) # remove file from source

```

---

