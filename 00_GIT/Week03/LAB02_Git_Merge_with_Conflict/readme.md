
## Git Lab Exercise: Resolving Merge Conflicts

### Objective
Learn how to resolve a merge conflict in Git that occurs when changes in two branches are incompatible.

### Setup

1. Open the terminal.
2. Navigate to a suitable directory for your project.
3. Initialize a new Git repository:

   ```bash
   git init
   ```

### Task 1: Create Initial Commit in `master` Branch

1. Create a file `conflict.txt` and make the initial commit:

   ```bash
   echo "Line 1: This is the start of the document." > conflict.txt
   git add conflict.txt
   git commit -m "Initial commit on master"
   ```

### Task 2: Add More Commits to `master` Branch

1. Add a new line to `conflict.txt` and commit:

   ```bash
   echo "Line 2: Additional line in master branch." >> conflict.txt
   git add conflict.txt
   git commit -m "Second commit on master"
   ```

2. Make another change and commit:

   ```bash
   echo "Line 3: Further changes in master branch." >> conflict.txt
   git add conflict.txt
   git commit -m "Third commit on master"
   ```

 3. Display the commit history:

   ```
   cat conflict.txt
   ```

   check git log
    
    git log --oneline
    


### Task 3: Create `new_branch` and Add Commits

1. Create a new branch named `new_branch` and switch to it:

   ```bash
   git checkout -b new_branch
   ```

2. Make changes to `conflict.txt` that will conflict with `master`:

   ```bash
   echo "Line 1 (new branch): This line will cause a merge conflict." > conflict.txt
   git add conflict.txt
   git commit -m "First commit on new_branch"
   ```

3. Add another conflicting line and commit:

   ```
   echo "Line 2 (new branch): This is another conflicting line." >> conflict.txt
   git add conflict.txt
   git commit -m "Second commit on new_branch"
   ```

  ### Task 4: add new commit in master branch

 1. Switch back to the `master` branch and Add Alpha commit:

  
   ```
   git switch master
   ```
   
   ```
   echo "Line Extra master : Add Alpha text " >> conflict.txt
   git add conflict.txt
   git commit -m "Alpha commit"
   ```



 2. Display the commit history:


   ```
   cat conflict.txt
   ```

   check git log

    
    git log --oneline
    
    


### Task 5: Merge `new_branch` into `master` and Resolve Conflict

1. Switch back to the `master` branch:

   ```bash
   git checkout master
   ```

2. Attempt to merge `new_branch` into `master`:

   ```bash
   git merge new_branch
   ```

   A merge conflict will occur because of the incompatible changes.

```
<<<<<<< HEAD
Line 1: This is the start of the document.
Line 2: Additional line in master branch.
Line 3: Further changes in master branch.
Line Extra master : Add Alpha text 
=======
Line 1 (new branch): This line will cause a merge conflict.
Line 2 (new branch): This is another conflicting line.
>>>>>>> new_branch

```


3. Manually resolve the conflict by editing the file to keep the lines you want.
4. After resolving the conflict, stage the changes:

   ```bash
   git add conflict.txt
   ```

5. Complete the merge with a commit:

   ```bash
   git commit -m "Resolved merge conflict between master and new_branch"
   ```

### Conclusion

You have successfully created and resolved a merge conflict. This is a common situation when working on a team or when multiple changes happen to the same part of a file in different branches.

