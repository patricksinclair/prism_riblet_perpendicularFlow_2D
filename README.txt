This system is used for 2D simulations of the perpendicular flow case.  2D is much less computationally expensive so can run simulations for much longer.

To convert to 2D:

- Need to use "libs ("libdynamicRefine2D.so");" in system/controlDict for 2D adaptive mesh refinement.

- Need to edit constant/dynamicMeshDict so that it uses the correct "dynamicRefine2DFvMesh;" format.

- No. of z-cells must be set to 1.

- Perpendicular flow, so frontWall and backWall must be type "empty".  This can be achieved just by commenting out their entries.

- Likewise, need to comment out the frontWall and backWall entries in the 0/* boundary condition files.

- Will need to edit the postProcessing python scripts too.












/////////// BELOW IS RELEVANT FOR THE 3D CASE THIS WAS COPIED FROM, GIST OF IT SHOULD STILL BE RELEVANT /////////////

This is the setup used for the perpendicular flow runs.  The boundary conditions for p and U have been swapped so that the outlet is now on the rightWall instead of the rear one.
Also the flow direction is now in the x-axis rather than z.

There is a minimal difference in the area (it's not perfectly square), so this might also be something worth remembering depending on what the results look like.


This version is the one which will be used for the big runs now.  It's pretty similar to the previous version, but things have been tidied up a bit.
Mesh and geometry are now sorted.
This is the parallel flow, the riblets are aligned in the z-direction, and the flow is in the z-direction.

As a test, we'll set the side wall velocity boundary conditions to zeroGradient instead of slip, and see if this works.
The reason being, for the 45 degree flow case, there might be some biofilm that gets pushed to the side, so having them as zeroGradient
might stop there being any weird edge effects.
Or it might make things much worse, lets find out.
