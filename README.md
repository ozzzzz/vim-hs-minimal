# vim-hs-minimal
Minimal configurations for vim

## Steps

* Install [vim-pathogen](https://github.com/tpope/vim-pathogen)
  Don't forget to add lines in `~/.vimrc`:
  ```execute pathogen#infect()
     syntax on
     filetype plugin indent on
  ```

* Install [vim-syntastic](https://github.com/vim-syntastic/syntastic)

* Install [stylish-haskell](https://github.com/jaspervdj/stylish-haskell) with `stack install stylish-haskell`

* Install [hlint](https://github.com/ndmitchell/hlint#readme) with `stack install hlint`

* Install [NERDTree](https://github.com/scrooloose/nerdtree)

* Install [vim-airline](https://github.com/vim-airline/vim-airline)

* If you have problems with copy to clickboard on MacOS, then reinstall vim with command `brew install vim --with-client-server`.

* Add some bindings and settings (`~/.vimrc`):
```
" enable plugins
execute pathogen#infect()
syntax on
filetype plugin indent on

" tab settings
set smartindent
set expandtab
set shiftwidth=4
set tabstop=4

" mouse settings
:set mousemodel=extend
:set mouse=a

" copy and paste to system clipboard
vmap <Leader>y "+y
vmap <Leader>d "+d
nmap <Leader>p "+p
nmap <Leader>P "+P
vmap <Leader>p "+p
vmap <Leader>P "+P

" buffers settings
map <S-tab> :bp<CR>
map <tab> :bn<CR>
" next to close buffer without hassle: https://stackoverflow.com/questions/31805805/vim-close-buffer-with-nerdtree
nnoremap c :bp\|bd #<CR>


" PLUGINS SETTINGS

" vim-syntastic
set statusline+=%#warningmsg#
set statusline+=%{SyntasticStatuslineFlag()}
set statusline+=%*
let g:syntastic_always_populate_loc_list = 1
" let g:syntastic_auto_loc_list = 1
let g:syntastic_check_on_open = 1
let g:syntastic_check_on_wq = 0

" Airline
let g:airline#extensions#tabline#enabled = 1

" NERDTree
map <C-n> :NERDTreeToggle<CR>

" stylish-haskell
map <C-c> :%!stylish-haskell<CR>
```
