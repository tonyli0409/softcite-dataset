---
title: "Working on Softcite Data Files"
---
This is the basic information you need to get into the Howison lab server and to commit your changes.

##Accessing the lab server
This is how you can access the lab's server where your work is stored:

###Macs:
`$ ssh <username>@howisonlab.ischool.utexas.edu`

Note that a $ preceding a line is just indicating that you type everything after that. Do not type the $ yourself.

###Windows (using Putty):
Enter the following in the server field: howisonlab.ischool.utexas.edu. Click connect and then enter your username and password into the command line window that opens.

###Access from off campus
When you need to connect to the server from home, you'll need to use a VPN. The business school has useful instructions (https://www.mccombs.utexas.edu/Tech/Web-Team/Sitecore-Training/VPN-login).  You will need to download CISCO AnyConnect, regardless of what kind of computer you use. Note that when you put your "second password" in you won't be typing your password for a second time, but entering "push," "SMS," or "phone" according to the instructions below that field.

##Moving to the right repo
Once you've logged onto the server, you'll need to move to the correct folder. For now, we're only working on softcite work, so you'll change directories in the terminal:

`$ cd softcite-dataset/`

##Opening the server in Atom
To edit your server files, you'll need to open the folder that you made your .ftpconfig file in Atom. Then, you can open the FTP remote pane by going to packages>ftp remote>toggle. Then, from the pane that opens, you can hit connect. You can collapse the pane that has your .ftpconfig file in it—you won't need that.

##Checking for errors
Before committing, you will need to confirm that there are no problems with your files. You will run the command pytest, and repair any errors if necessary.


`$ pytest`
Check if there are any errors. If a file has an error, it will be shown under “Captured stdout call” and look like:

`Parsing data/individuals-XXXXX/#######.ttl
Seek line numbers for errors with:
python3 code/parseTurtle.py -f data/individuals- XXXXX/#######.ttl
Use ctrl-G to jump to line number`

To find out exactly where the error in that particular file is, copy the line line that begins with `python3 code/`… and run that as a command:

`$ python3 code/parseTurtle.py -f data/individuals- XXXXX/#######.ttl`

The command will run and spew out a bunch of stuff that ends with an error saying something like:

`rdflib.plugins.parsers.notation3.BadSyntax: at line 330 of <>:`

In Atom, *if this was a file you edited*, visit the line number in the file (which was named after running pytest) and resolve the error, save, commit, and push as described below.

##Committing changes
When you need to save your changes, you will make a commit. The first step is to check what files have been changed. Then, add the files that are in your individuals folder (don't add anything in the cache or anything you don't remember modifying). Then double check you've added everything you need. Then make a commit and include a message. Finally, you'll push your changes up to your Github repo. Step by step:

`$ git status`
view which files were modified

`$ git add <name of modified file>`
add the files you want

`$ git status`
view which files were modified to check you got everything

`$ git commit –m “<message content>”`
enter your commit message

`$ git push origin master`
push commit up to Github

After you have completely finished coding an article, you can make a pull request. To do that, visit your repo on Github and click the "New Pull Request" button.

##Requesting a new article
When you have finished coding one article and committed your work, you can request another article to work on.

From the terminal, execute the following command:

`$ python3 code/getNextContentAnalysisAssignment.py`

A new file will be added to your individuals folder. You may need to right click on it and hit refresh to make the new file appear. The new file will contain the prefixes and article block for your new assignment.

##Github tutorials:
There are many free tutorials on how to use git that might be useful.

https://www.codecademy.com/learn/learn-git
http://gitimmersion.com/
https://help.github.com/

Git cheat sheet: https://education.github.com/git-cheat-sheet-education.pdf