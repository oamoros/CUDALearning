# cudaMemset weird behavior in cuda 9.1 Open
I found that cudaMemsetAsynch does not respect the fifo nature of CUDA Streams, and also prevents the overlapping of memory transfers and computation, under certain conditions. I want to explore this issues, and possible kernel implementations that might prove to be faster than cudaMemsetAsynch.

The first version of the code, already reproduces the problem. It is observable with NSIGHT Visual Studio. Despite the kernel was enqueued first, the cudaMemsetAsync is executing first.

I may use this code, with some extra politeness (cuda error checks and so on), to file a bug to NVIDIA.