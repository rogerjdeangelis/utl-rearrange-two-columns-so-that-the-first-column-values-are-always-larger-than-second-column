# utl-rearrange-two-columns-so-that-the-first-column-values-are-always-larger-than-second-column
Re-arrange two columns so that the first column values are always larger than second column   
    Re-arrange two columns so that the first column values are always larger than second column                                                 
                                                                                                                                                
    github                                                                                                                                      
    https://tinyurl.com/ycsuufmn                                                                                                                
    https://github.com/rogerjdeangelis/utl-rearrange-two-columns-so-that-the-first-column-values-are-always-larger-than-second-column           
                                                                                                                                                
    stackoverflow                                                                                                                               
    https://tinyurl.com/y9q4bbt6                                                                                                                
    https://stackoverflow.com/questions/62090306/rearrange-two-columns-so-that-the-first-column-values-are-always-larger-in-r                   
                                                                                                                                                
                                                                                                                                                
    * Originally v2 was always larger than v1 but the data got scrambled.                                                                       
    * I need to rearange the colums so the v2 is always larger than v1 and use all the data.                                                    
    * I need to put the back into the correct order.                                                                                            
                                                                                                                                                
     Two solutions                                                                                                                              
           a. sas                                                                                                                               
           b. R                                                                                                                                 
              R can sort multiple columns in place                                                                                              
                                                                                                                                                
    options validvarname=upcase;                                                                                                                
    libname sd1 "d:/sd1";                                                                                                                       
    data sd1.have;                                                                                                                              
      input id  V1 V2;                                                                                                                          
    cards4;                                                                                                                                     
     36  63                                                                                                                                     
     01  73                                                                                                                                     
     96  59                                                                                                                                     
     22  42                                                                                                                                     
    203 185                                                                                                                                     
    127 197                                                                                                                                     
    183  60                                                                                                                                     
    159 200                                                                                                                                     
     52 128                                                                                                                                     
     63  27                                                                                                                                     
     19  02                                                                                                                                     
     67 178                                                                                                                                     
     14 174                                                                                                                                     
    171  99                                                                                                                                     
     52 168                                                                                                                                     
    195 121                                                                                                                                     
    199  24                                                                                                                                     
    118 153                                                                                                                                     
    166  24                                                                                                                                     
    149 209                                                                                                                                     
    ;;;;                                                                                                                                        
    run;quit;                                                                                                                                   
                                                                                                                                                
    *            _               _                                                                                                              
      ___  _   _| |_ _ __  _   _| |_                                                                                                            
     / _ \| | | | __| '_ \| | | | __|                                                                                                           
    | (_) | |_| | |_| |_) | |_| | |_                                                                                                            
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                                                           
                    |_|                                                                                                                         
    ;                                                                                                                                           
                                                                                                                                                
                                                                                                                                                
    WORK.WANT_SAS total obs=20 (same output SAs and R)                                                                                          
                 | RULES                                                                                                                        
      V2    V1   |                                                                                                                              
                 |                                                                                                                              
       2     1   |  V2 is always greater than V1                                                                                                
      24    14   |  This was the original order?                                                                                                
      24    19   |  Originally V2 inclued a stck dividend                                                                                       
      27    22   |                                                                                                                              
      42    36   |                                                                                                                              
      59    52   |                                                                                                                              
      60    52   |                                                                                                                              
      63    63   |                                                                                                                              
      73    67   |                                                                                                                              
      99    96   |                                                                                                                              
     121   118   |                                                                                                                              
     128   127   |                                                                                                                              
     153   149   |                                                                                                                              
     168   159   |                                                                                                                              
     174   166   |                                                                                                                              
     178   171   |                                                                                                                              
                                                                                                                                                
     185   183   |                                                                                                                              
     197   195   |                                                                                                                              
     200   199   |                                                                                                                              
     209   203   |                                                                                                                              
                                                                                                                                                
    *          _       _   _                                                                                                                    
     ___  ___ | |_   _| |_(_) ___  _ __  ___                                                                                                    
    / __|/ _ \| | | | | __| |/ _ \| '_ \/ __|                                                                                                   
    \__ \ (_) | | |_| | |_| | (_) | | | \__ \                                                                                                   
    |___/\___/|_|\__,_|\__|_|\___/|_| |_|___/                                                                                                   
                                                                                                                                                
      __ _     ___  __ _ ___                                                                                                                    
     / _` |   / __|/ _` / __|                                                                                                                   
    | (_| |_  \__ \ (_| \__ \                                                                                                                   
     \__,_(_) |___/\__,_|___/                                                                                                                   
                                                                                                                                                
    ;                                                                                                                                           
                                                                                                                                                
    proc sort data=sd1.have out=havRan1(keep=v1);                                                                                               
      by v1;                                                                                                                                    
    run;quit;                                                                                                                                   
                                                                                                                                                
    proc sort data=sd1.have out=havRan2(keep=v2);                                                                                               
      by v2;                                                                                                                                    
    run;quit;                                                                                                                                   
                                                                                                                                                
    data want_sas;                                                                                                                              
      merge havRan1 havRan2;                                                                                                                    
    run;quit;                                                                                                                                   
                                                                                                                                                
                                                                                                                                                
    *_        ____                                                                                                                              
    | |__    |  _ \                                                                                                                             
    | '_ \   | |_) |                                                                                                                            
    | |_) |  |  _ <                                                                                                                             
    |_.__(_) |_| \_\                                                                                                                            
                                                                                                                                                
    ;                                                                                                                                           
                                                                                                                                                
    * R can sort mutiple columns in place;                                                                                                      
                                                                                                                                                
    %utl_submit_r64('                                                                                                                           
    library(haven);                                                                                                                             
    library(SASxport);                                                                                                                          
    want<-read_sas("d:/sd1/have.sas7bdat");                                                                                                     
    want[] <- apply(want, 2, sort);                                                                                                             
    write.xport(want,file="d:/xpt/want.xpt");                                                                                                   
    ');                                                                                                                                         
                                                                                                                                                
    libname xpt xport "d:/xpt/want.xpt";                                                                                                        
    data want;                                                                                                                                  
      set xpt.want;                                                                                                                             
    run;quit;                                                                                                                                   
    libname xpt clear;                                                                                                                          
                                                                                                                                                
