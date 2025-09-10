The .mat files in each folder consist of the data collected directly from measurement: probe force, probe displacement and scan plane RF data. 
Each folder has the following .mat files. Our naming convention refers to the bmode image, however we note the provided data file is the RF echo frames. 

all_bmode.mat: 
	Contains: 
		-> bmode: Matrix of raw RF data of size NxMx(S+1), where N is the axial samples, M is the lateral samples and S is the number of steps

bmode_image_axes_mm.mat: 
	Contains: 
		-> bmode_axial_vec: Axial axis of size 1xN, where N is the axial samples. Units are in mm. bmode_axial_vec(1) is the top of the phantom. bmode_axial_vec(end) is the bottom. 
		-> bmode_lateral_vec: Lateral axis of size 1xM, where M is the lateral samples. Units are in mm. bmode_lateral_vec(1) is the left side of the phantom. bmode_lateral_vec(end) is the right side. 
	Details: When registering the image axes from US to Abaqus, we center each axis on 0 such that the center of the phantom represents the origin (0,0).    

bmode_image_parameters.mat: 
	Contains: 
		-> Fc: center frq of US probe (Hz)
		-> Fs: sampling frq of US probe (Hz)
		-> sos_ms: speed of sound in m/s
		-> tx_dist_mm: focal depth in mm
		-> lat_foot: lateral tx footprint in mm
		-> elev_foot: elevational tx footprint in mm 
		-> tx_center_elev: The elevational (z) axis spans -25 to 25 mm. This value indicates where on that axis the centerline of the probe is (in mm).   

probe_force_displacement_data.mat: 
	Contains: 
		-> displacement_curve: axial probe displacements of size 1x(S+1). If we took 15 steps, we have 16 displacement_curve values that start at 0. 
		-> force_curve: axial probe force measurements of size 1x(S+1). Measurements describe the total axial surface force over the surface area of the compressor.   
		-> num_steps: S
	Details: Force and displacement were compressive, but we include them as positive values. If you set this up in ABAQUS, recognize that the sign of the applied force and displacement would need to match the ABAQUS coordinate system for compression. 
	

Folders:
two_sphere->the measurement plane from the fully gelatin two-sphere phantom. 

liver-> right_lobe-> the measurement plane from the right lobe of the liver-gelatin phantom containing the formalin lesion
	left_lobe->  the measurement plane from the left lobe of the liver-gelatin phantom representing uniform liver tissue. 
 