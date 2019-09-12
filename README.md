# git tools commands

1- Configure the author name and email address to be used with your commits.
Note that Git strips some characters (for example trailing periods) from user.name.
git config --global user.name "Sam Smith"
git config --global user.email sam@example.com

2- Create a new local repository
git init

3- Check out a repository
git clone /path/to/repository
ex. git clone username@host:/path/to/repository

4- Add files
Add one or more files to staging (index):

git add *
first goto that folder and make your chnages and then use 'git add *' commands

5- Commit
Commit changes to head (but not yet to the remote repository):

git commit -m "Commit message"

Commit any files you've added with git add, and also commit any files you've changed since then:
git commit -a

6- Push
Send changes to the master branch of your remote repository:
git push origin master

7- status
List the files you've changed and those you still need to add or commit:

git status

8- connect to a remote repository
If you haven't connected your local repository to a remote server, add the server to be able to push to it:

git remote add origin <server>

to check List all currently configured remote repositories:
git remote -v

9- Branches
Create a new branch and switch to it:	
git checkout -b <branchname>

Switch from one branch to another:	
git checkout <branchname>

List all the branches in your repo, and also tell you what branch you're currently in:	
git branch

Delete the feature branch:	
git branch -d <branchname>

Push the branch to your remote repository, so others can use it:	
git push origin <branchname>

Push all branches to your remote repository:	
git push --all origin

Delete a branch on your remote repository:	
git push origin :<branchname>

9-Update from the remote repository
Fetch and merge changes on the remote server to your working directory:	
git pull

To merge a different branch into your active branch:	
git merge <branchname>

View all the merge conflicts:
View the conflicts against the base file:

Preview changes, before merging:
git diff
git diff --base <filename>
git diff <sourcebranch> <targetbranch>

After you have manually resolved any conflicts, you mark the changed file:	
git add <filename>

10- Tags
You can use tagging to mark a significant changeset, such as a release:	
git tag 1.0.0 <commitID>

CommitId is the leading characters of the changeset ID, up to 10, but must be unique. Get the ID using:	
git log

Push all tags to remote repository:	
git push --tags origin
11- Undo local changes
If you mess up, you can replace the changes in your working tree with the last content in head:
Changes already added to the index, as well as new files, will be kept.

git checkout -- <filename>

Instead, to drop all your local changes and commits, fetch the latest history from the server and point your local master branch at it, do this:	
git fetch origin

git reset --hard origin/master

11- Search
Search the working directory for foo():	
git grep "foo()"

12-Viewing project history
git log

If you also want to see complete diffs at each step, use

git log -p

Often the overview of the change is useful to get a feel of each step

git log --stat --summary

13-Exploring history
git log
commit c82a22c39cbc32576f64f5c6b3f24b99ea8149c7
Author: Junio C Hamano <junkio@cox.net>
Date:   Tue May 16 17:18:22 2006 -0700

    merge-base: Clarify the comments on post processing.
	
We can give this name to git show to see the details about this commit.

git show c82a22c39cbc32576f64f5c6b3f24b99ea8149c7

git show HEAD^  # to see the parent of HEAD
git show HEAD^^ # to see the grandparent of HEAD
git show HEAD~4 # to see the great-great grandparent of HEAD	


git log v2.5..v2.6            # commits between v2.5 and v2.6
git log v2.5..                # commits since v2.5
git log --since="2 weeks ago" # commits from the last 2 weeks
git log v2.5.. Makefile       # commits since v2.5 which modify
							  # Makefile
							  
14- git merge
View file conflicts in a merge tool. Default is vimdiff
git mergetool
Assign a GUI tool:
Meld:
git config --global merge.tool meld
git config --global mergetool.meld.cmd 'meld --diff $LOCAL $BASE $REMOTE --output $MERGED'
or: meld $LOCAL $MERGED $REMOTE --output $MERGED
or: meld $LOCAL $BASE $REMOTE --output $MERGED
(preference of three panes ordered left to right)

if user are using vimdiff then use below command.
vimdiff	- edit two, three or four versions of a file with Vim and show differences
vimdiff [options] file1 file2 [file3 [file4]]
							  
