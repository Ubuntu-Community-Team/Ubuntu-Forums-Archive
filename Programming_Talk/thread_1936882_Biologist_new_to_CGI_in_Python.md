---
title: "Biologist new to CGI in Python"
date: 2012-03-06
forum: Programming Talk
---

### Post by chimpsarehungry on 2012-03-06
Hi,

I would greatly appreciate some help for a beginner to python programming. 

There is a server here that I am trying to write scripts to access:
[http://consurf.tau.ac.il/index_full_form_PROT.php](http://consurf.tau.ac.il/index_full_form_PROT.php)

I have been able to fill out the form simple in the url like this:

Submit_seq = "http://consurf.tau.ac.il/cgi-bin/new_consurf.cgi?Run_Number=NONE&MAX_FILE_SIZE=2000000&PDB_yes_no=no&MSA_yes_no=no&FASTA_text=%s&MSAprogram=MAFFT&proteins_DB=UNIREF90&MAX_NUM_HOMOL=150&MAX_REDUNDANCY=95&MIN_IDENTITY=35&ITERATIONS=1&E_VALUE=0.0001&Homolog_search_algorithm=BLAST&ALGORITHM=Bayes&SUB_MATRIX=JTT&submitForm=Submit" % (text,)

The %s after FASTA_text is connected to a variable of which I am looping through many files of text. 

The major problem I am having now is uploading a file. On that server there is an option to upload a multiple sequence alignment (MSA) when I do that and look at the HTTP headers I see this:

Content-Disposition: form-data; name="MSA_yes_no"

yes
-----------------------------178448449274243042114807987
Content-Disposition: form-data; name="msa_FILE"; filename="MSAfromnakai.ashx.clustalw"
Content-Type: application/octet-stream

And then below is the text of the file I uploaded. I tried pasting that text into the url for msa_FILE=   but it said the URL length was too long for the server. That probably wouldnt work anyway because it needs the file uploaded. Do you have any ideas? 

Here is the function I am using to insert the variable file text inside the url. Is it even possible to include the upload command in the url? 

def file_exporter():

    path = "/Users/chimpsarehungry/Desktop/MSAtests"
    MSAtests = os.listdir(path)

    for MSA in MSAtests:
        file = os.path.join(path, MSA)
        MSAread = file
         
        Submit_seq = "http://consurf.tau.ac.il/cgi-bin/new_consurf.cgi?Run_Number=NONE&MAX_FILE_SIZE=20000000000&PDB_yes_no=no&MSA_yes_no=yes&msa_FILE=%s&filename=MSAfromnakai1&msa_SEQNAME=AAV2&Homolog_search_algorithm=BLAST&ALGORITHM=Bayes&SUB_MATRIX=JTT&submitForm=Submit" % (MSAread,)

Thank you much.

Shane

---

### Post by Some Penguin on 2012-03-07
File uploads and forms tend to be associated with multipart POST requests.

See --

[http://www.doughellmann.com/PyMOTW/urllib2/#uploading-files]("http://www.doughellmann.com/PyMOTW/urllib2/#uploading-files")

for instance.

---

