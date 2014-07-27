yasnippet-csharp
================

A collection of C# snippets for yasnippet

The following elisp snippet is required for namespace generation. (Thanks to  http://cupfullofcode.com/snippet-expansion-with-yasnippet/)

```elisp
(defun find-git-repo (dir)
  (if (string= "/" dir)
      nil
    (if (file-exists-p (expand-file-name "../.git/" dir))
        dir
      (find-git-repo (expand-file-name "../" dir)))))


(defun file-path-to-namespace ()
  (interactive)
  (let (
        (root (find-project-root))
        (base (file-name-nondirectory buffer-file-name))
        )
    (substring (replace-regexp-in-string "/" "\." (substring buffer-file-name (length root) (* -1 (length base))) t t) 0 -1)
    )
  )
```
