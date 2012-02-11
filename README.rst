==========================
 reStructuredText checker
==========================


Usage
-----

::

  rstcheck.py path/to/file.rst


Using rstcheck with flymake
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Put the following in your Emacs setting and replace
`"path/to/rstcheck.py"` with the real path::

  (defun flymake-rst-init ()
    (let* ((temp-file (flymake-init-create-temp-buffer-copy
                       'flymake-create-temp-inplace))
           (local-file (file-relative-name
                        temp-file
                        (file-name-directory buffer-file-name))))
      (list "path/to/rstcheck.py" (list local-file))))

  (add-to-list 'flymake-allowed-file-name-masks
               '("\\.rst\\'" flymake-rst-init))
  (add-to-list 'flymake-allowed-file-name-masks
               '("\\.rest\\'" flymake-rst-init))
