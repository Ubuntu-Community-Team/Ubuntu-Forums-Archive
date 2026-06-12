---
title: "umfpack installed, but undefined reference"
date: 2007-02-13
forum: Programming Talk
---

### Post by c174 on 2007-02-13
I just tried to migrate a c++ program written under windows to linux. I was happy to see that UMFPACK (sparse matrix package) on which the program depends can be installed using Synaptic.

However, during linkage I get errors:

$ g++ -o main *.o ../plotting2/*.o  -lglut -lumfpack -lamd
sparse.o: In function `SparseMatrix::solve(NRVec<double> const&, NRVec<double>&)':
sparse.cpp:(.text+0x330): undefined reference to `umfpack_di_solve(int, int const*, int const*, double const*, double*, double const*, void*, double const*, double*)'
sparse.o: In function `SparseMatrix::factor()':
sparse.cpp:(.text+0x61e): undefined reference to `umfpack_di_triplet_to_col(int, int, int, int const*, int const*, double const*, int*, int*, double*, int*)'
sparse.cpp:(.text+0x728): undefined reference to `umfpack_di_symbolic(int, int, int const*, int const*, double const*, void**, double const*, double*)'
sparse.cpp:(.text+0x7c1): undefined reference to `umfpack_di_numeric(int const*, int const*, double const*, void*, void**, double const*, double*)'
sparse.cpp:(.text+0x80f): undefined reference to `umfpack_di_free_symbolic(void**)'
sparse.o: In function `SparseMatrix::clear()':
sparse.cpp:(.text+0xed9): undefined reference to `umfpack_di_free_numeric(void**)'

How can this be? libumfpack.a is found by g++ Do I need to compile umfpack myself (as under windows/cygwin)?

Any help is most welcome!

---

### Post by c174 on 2007-02-13
Running: ar t /usr/lib/libumfpack.a gives 

umf_i_analyze.o
umf_i_apply_order.o
umf_i_colamd.o
umf_i_free.o
umf_i_fsize.o
umf_i_is_permutation.o
umf_i_malloc.o
umf_i_realloc.o
umf_i_report_perm.o
umf_i_singletons.o
umf_l_analyze.o
umf_l_apply_order.o
umf_l_colamd.o
umf_l_free.o
umf_l_fsize.o
umf_l_is_permutation.o
umf_l_malloc.o
umf_l_realloc.o
umf_l_report_perm.o
umf_l_singletons.o
umfpack_gn_timer.o
umfpack_gn_tictoc.o
umf_di_lhsolve.o
umf_di_uhsolve.o
umf_di_triplet_map_nox.o
umf_di_triplet_nomap_x.o
umf_di_triplet_nomap_nox.o
umf_di_triplet_map_x.o
umf_di_assemble_fixq.o
umf_di_store_lu_drop.o
umf_di_assemble.o
umf_di_blas3_update.o
umf_di_build_tuples.o
umf_di_create_element.o
umf_di_dump.o
umf_di_extend_front.o
umf_di_garbage_collection.o
umf_di_get_memory.o
umf_di_init_front.o
umf_di_kernel.o
umf_di_kernel_init.o
umf_di_kernel_wrapup.o
umf_di_local_search.o
umf_di_lsolve.o
umf_di_ltsolve.o
umf_di_mem_alloc_element.o
umf_di_mem_alloc_head_block.o
umf_di_mem_alloc_tail_block.o
umf_di_mem_free_tail_block.o
umf_di_mem_init_memoryspace.o
umf_di_report_vector.o
umf_di_row_search.o
umf_di_scale_column.o
umf_di_set_stats.o
umf_di_solve.o
umf_di_symbolic_usage.o
umf_di_transpose.o
umf_di_tuple_lengths.o
umf_di_usolve.o
umf_di_utsolve.o
umf_di_valid_numeric.o
umf_di_valid_symbolic.o
umf_di_grow_front.o
umf_di_start_front.o
umf_di_2by2.o
umf_di_store_lu.o
umf_di_scale.o
umfpack_di_wsolve.o
umfpack_di_col_to_triplet.o
umfpack_di_defaults.o
umfpack_di_free_numeric.o
umfpack_di_free_symbolic.o
umfpack_di_get_numeric.o
umfpack_di_get_lunz.o
umfpack_di_get_symbolic.o
umfpack_di_get_determinant.o
umfpack_di_numeric.o
umfpack_di_qsymbolic.o
umfpack_di_report_control.o
umfpack_di_report_info.o
umfpack_di_report_matrix.o
umfpack_di_report_numeric.o
umfpack_di_report_perm.o
umfpack_di_report_status.o
umfpack_di_report_symbolic.o
umfpack_di_report_triplet.o
umfpack_di_report_vector.o
umfpack_di_solve.o
umfpack_di_symbolic.o
umfpack_di_transpose.o
umfpack_di_triplet_to_col.o
umfpack_di_scale.o
umfpack_di_load_numeric.o
umfpack_di_save_numeric.o
umfpack_di_load_symbolic.o
umfpack_di_save_symbolic.o
umf_dl_lhsolve.o
umf_dl_uhsolve.o
umf_dl_triplet_map_nox.o
umf_dl_triplet_nomap_x.o
umf_dl_triplet_nomap_nox.o
umf_dl_triplet_map_x.o
umf_dl_assemble_fixq.o
umf_dl_store_lu_drop.o
umf_dl_assemble.o
umf_dl_blas3_update.o
umf_dl_build_tuples.o
umf_dl_create_element.o
umf_dl_dump.o
umf_dl_extend_front.o
umf_dl_garbage_collection.o
umf_dl_get_memory.o
umf_dl_init_front.o
umf_dl_kernel.o
umf_dl_kernel_init.o
umf_dl_kernel_wrapup.o
umf_dl_local_search.o
umf_dl_lsolve.o
umf_dl_ltsolve.o
umf_dl_mem_alloc_element.o
umf_dl_mem_alloc_head_block.o
umf_dl_mem_alloc_tail_block.o
umf_dl_mem_free_tail_block.o
umf_dl_mem_init_memoryspace.o
umf_dl_report_vector.o
umf_dl_row_search.o
umf_dl_scale_column.o
umf_dl_set_stats.o
umf_dl_solve.o
umf_dl_symbolic_usage.o
umf_dl_transpose.o
umf_dl_tuple_lengths.o
umf_dl_usolve.o
umf_dl_utsolve.o
umf_dl_valid_numeric.o
umf_dl_valid_symbolic.o
umf_dl_grow_front.o
umf_dl_start_front.o
umf_dl_2by2.o
umf_dl_store_lu.o
umf_dl_scale.o
umfpack_dl_wsolve.o
umfpack_dl_col_to_triplet.o
umfpack_dl_defaults.o
umfpack_dl_free_numeric.o
umfpack_dl_free_symbolic.o
umfpack_dl_get_numeric.o
umfpack_dl_get_lunz.o
umfpack_dl_get_symbolic.o
umfpack_dl_get_determinant.o
umfpack_dl_numeric.o
umfpack_dl_qsymbolic.o
umfpack_dl_report_control.o
umfpack_dl_report_info.o
umfpack_dl_report_matrix.o
umfpack_dl_report_numeric.o
umfpack_dl_report_perm.o
umfpack_dl_report_status.o
umfpack_dl_report_symbolic.o
umfpack_dl_report_triplet.o
umfpack_dl_report_vector.o
umfpack_dl_solve.o
umfpack_dl_symbolic.o
umfpack_dl_transpose.o
umfpack_dl_triplet_to_col.o
umfpack_dl_scale.o
umfpack_dl_load_numeric.o
umfpack_dl_save_numeric.o
umfpack_dl_load_symbolic.o
umfpack_dl_save_symbolic.o
umf_zi_lhsolve.o
umf_zi_uhsolve.o
umf_zi_triplet_map_nox.o
umf_zi_triplet_nomap_x.o
umf_zi_triplet_nomap_nox.o
umf_zi_triplet_map_x.o
umf_zi_assemble_fixq.o
umf_zi_store_lu_drop.o
umf_zi_assemble.o
umf_zi_blas3_update.o
umf_zi_build_tuples.o
umf_zi_create_element.o
umf_zi_dump.o
umf_zi_extend_front.o
umf_zi_garbage_collection.o
umf_zi_get_memory.o
umf_zi_init_front.o
umf_zi_kernel.o
umf_zi_kernel_init.o
umf_zi_kernel_wrapup.o
umf_zi_local_search.o
umf_zi_lsolve.o
umf_zi_ltsolve.o
umf_zi_mem_alloc_element.o
umf_zi_mem_alloc_head_block.o
umf_zi_mem_alloc_tail_block.o
umf_zi_mem_free_tail_block.o
umf_zi_mem_init_memoryspace.o
umf_zi_report_vector.o
umf_zi_row_search.o
umf_zi_scale_column.o
umf_zi_set_stats.o
umf_zi_solve.o
umf_zi_symbolic_usage.o
umf_zi_transpose.o
umf_zi_tuple_lengths.o
umf_zi_usolve.o
umf_zi_utsolve.o
umf_zi_valid_numeric.o
umf_zi_valid_symbolic.o
umf_zi_grow_front.o
umf_zi_start_front.o
umf_zi_2by2.o
umf_zi_store_lu.o
umf_zi_scale.o
umfpack_zi_wsolve.o
umfpack_zi_col_to_triplet.o
umfpack_zi_defaults.o
umfpack_zi_free_numeric.o
umfpack_zi_free_symbolic.o
umfpack_zi_get_numeric.o
umfpack_zi_get_lunz.o
umfpack_zi_get_symbolic.o
umfpack_zi_get_determinant.o
umfpack_zi_numeric.o
umfpack_zi_qsymbolic.o
umfpack_zi_report_control.o
umfpack_zi_report_info.o
umfpack_zi_report_matrix.o
umfpack_zi_report_numeric.o
umfpack_zi_report_perm.o
umfpack_zi_report_status.o
umfpack_zi_report_symbolic.o
umfpack_zi_report_triplet.o
umfpack_zi_report_vector.o
umfpack_zi_solve.o
umfpack_zi_symbolic.o
umfpack_zi_transpose.o
umfpack_zi_triplet_to_col.o
umfpack_zi_scale.o
umfpack_zi_load_numeric.o
umfpack_zi_save_numeric.o
umfpack_zi_load_symbolic.o
umfpack_zi_save_symbolic.o
umf_zl_lhsolve.o
umf_zl_uhsolve.o
umf_zl_triplet_map_nox.o
umf_zl_triplet_nomap_x.o
umf_zl_triplet_nomap_nox.o
umf_zl_triplet_map_x.o
umf_zl_assemble_fixq.o
umf_zl_store_lu_drop.o
umf_zl_assemble.o
umf_zl_blas3_update.o
umf_zl_build_tuples.o
umf_zl_create_element.o
umf_zl_dump.o
umf_zl_extend_front.o
umf_zl_garbage_collection.o
umf_zl_get_memory.o
umf_zl_init_front.o
umf_zl_kernel.o
umf_zl_kernel_init.o
umf_zl_kernel_wrapup.o
umf_zl_local_search.o
umf_zl_lsolve.o
umf_zl_ltsolve.o
umf_zl_mem_alloc_element.o
umf_zl_mem_alloc_head_block.o
umf_zl_mem_alloc_tail_block.o
umf_zl_mem_free_tail_block.o
umf_zl_mem_init_memoryspace.o
umf_zl_report_vector.o
umf_zl_row_search.o
umf_zl_scale_column.o
umf_zl_set_stats.o
umf_zl_solve.o
umf_zl_symbolic_usage.o
umf_zl_transpose.o
umf_zl_tuple_lengths.o
umf_zl_usolve.o
umf_zl_utsolve.o
umf_zl_valid_numeric.o
umf_zl_valid_symbolic.o
umf_zl_grow_front.o
umf_zl_start_front.o
umf_zl_2by2.o
umf_zl_store_lu.o
umf_zl_scale.o
umfpack_zl_wsolve.o
umfpack_zl_col_to_triplet.o
umfpack_zl_defaults.o
umfpack_zl_free_numeric.o
umfpack_zl_free_symbolic.o
umfpack_zl_get_numeric.o
umfpack_zl_get_lunz.o
umfpack_zl_get_symbolic.o
umfpack_zl_get_determinant.o
umfpack_zl_numeric.o
umfpack_zl_qsymbolic.o
umfpack_zl_report_control.o
umfpack_zl_report_info.o
umfpack_zl_report_matrix.o
umfpack_zl_report_numeric.o
umfpack_zl_report_perm.o
umfpack_zl_report_status.o
umfpack_zl_report_symbolic.o
umfpack_zl_report_triplet.o
umfpack_zl_report_vector.o
umfpack_zl_solve.o
umfpack_zl_symbolic.o
umfpack_zl_transpose.o
umfpack_zl_triplet_to_col.o
umfpack_zl_scale.o
umfpack_zl_load_numeric.o
umfpack_zl_save_numeric.o
umfpack_zl_load_symbolic.o
umfpack_zl_save_symbolic.o

So apparently the library has the names that are reported as "undefined reference". Is it possible to extract also the arguments for the *.o files?

Is it possible that the header file "umfpack.h" does not match the library?? (compilation is fine).

Oh - forgot to mention: I'm new to programming under linux. Please help me, if you have any suggestion. Thanks.

---

### Post by hod139 on 2007-02-13
I'm assuming you installed the *libumfpack4-dev *package and that you are using the headers located at 
usr/include/umfpack/

not anything else.  Otherwise, it looks like you are doing everything correctly.

---

### Post by c174 on 2007-02-13
Yes, that is what I did.

I just tried this small piece of code:

#include <umfpack/umfpack.h>

int main( int argc, char* argv[] ) {


	int n_row, n_col, nz, *Ti, *Tj, *Ap, *Ai, status, *Map ;
    	double *Tx, *Ax ;
    	status = umfpack_di_triplet_to_col (n_row, n_col, nz, Ti, Tj, Tx, Ap, Ai, Ax, Map) ;

	return 1;
}

However, compiling and linking gives me this

$ g++ -c testtest.cpp
$ g++ -o testmain testtest.o -lumfpack -lamd
testtest.o: In function `main':
testtest.cpp:(.text+0x57): undefined reference to `umfpack_di_triplet_to_col(int, int, int, int const*, int const*, double const*, int*, int*, double*, int*)'
collect2: ld returned 1 exit status

So compile is okay. But it won't link. Do I need to do something with ldconfig? (I am not familar with ldconfig)

---

### Post by c174 on 2007-02-13
I got a clue:

If I use gcc instead of g++ (and change the source file from *.cpp to .c) then  the small piece of code in the previous post works fine! So, it must be some problem with mixing c++ and c. However, looking at the header file "umfpack.h" it has an 'extern "c"' wrapper.

Mayby, there is a standard solution or hints for cases like this?

---

### Post by c174 on 2007-02-13
Sorry!!! My mistake - there is NOT an 'extern "C" '-clause in the "umfpack.h" header file! So that is why it didn't work with g++

This works:

```

extern "C" {
#include <umfpack/umfpack.h>
}

int main( int argc, char* argv[] ) {

	int n_row, n_col, nz, *Ti, *Tj, *Ap, *Ai, status, *Map ;
    	double *Tx, *Ax ;
    	status = umfpack_di_triplet_to_col (n_row, n_col, nz, Ti, Tj, Tx, Ap, Ai, Ax, Map) ;

	return 1;
}
```

With this for compiling/linking

$ g++ -c testtest.cpp
$ g++ -o testmain testtest.o -lumfpack -lamd


Thank you hod139 for responding to my post.

:)

---

### Post by hod139 on 2007-02-13
I wish I could say I helped!

On the topic of umfpack, have you seen [CSparse]("http://www.cise.ufl.edu/research/sparse/CSparse/"), and can you comment in general about existing sparse matrix libraries?  I am working on a project that deals with very large, but very sparse matrices and we are actually currently looking at available C/C++ libraries for sparse systems.  It seems there really are not that many choices available, and was wondering what you suggested.

---

### Post by c174 on 2007-02-14
> **hod139 said:**
> 
On the topic of umfpack, have you seen [CSparse]("http://www.cise.ufl.edu/research/sparse/CSparse/"), and can you comment in general about existing sparse matrix libraries?

What kind of problem are you solving? If you need to FACTOR a matrix (because you have multiple right hands sides) I would suggest UMFPACK or MUMPS. I never tried the latter one. UMPFACK can run with BLAS support - or without, but will be alot slower. Therefore a good implementation of BLAS is something to look for. I just took whatever Synaptic added as dependent packages... But under Windows I used ATLAS (Automatically Tuned BLAS). Another option is to use GOTO BLAS, which can be obtained for free for some applications - should be the best choice currently.

If you only have ONE right hand side, you might consider to use an iterative method. Performance can be very good, and small memory requirements. This is especially true if the matrix is symmetric (and even more if all eigen values are real). Have a look at the Numerical Recipes webpage [www.nr.com](www.nr.com). They provide code, which you can type in yourself in short time for several languages.

I am not familar with CSparse :-)

Hope this is helpful.

---

### Post by c174 on 2007-02-14
An overview of many direct methods

[http://www.cise.ufl.edu/research/sparse/codes/](http://www.cise.ufl.edu/research/sparse/codes/)

---

### Post by hod139 on 2007-02-14
Thanks!

---

