# gitconfig

These are my current git aliases. 

There are also some useful powershell functions

```
function touch {set-content -Path ($args[0]) -Value ($null)} 
Import-Module posh-git
Set-Location C:\dev\EpiServerCTM
new-item alias:g -value 'git'

function Delete-MergedBranches {
    git branch $Commit |
        ? { $_ -notmatch '(^\*)|(^. master$)' } |
        % { git branch -D $_.Substring(2) }
}

function DeleteBranches {
    git branch | %{$_.trim()} | ?{$_ -notmatch 'develop
' -and $_ -notmatch 'master'} | %{git branch -D $_}
}

function PullCurrentBranch {
    $branch= &git rev-parse --abbrev-ref HEAD 
    git pull origin $branch
}
```
