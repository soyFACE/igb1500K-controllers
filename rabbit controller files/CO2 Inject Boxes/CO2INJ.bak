#define UNIT_ID 0  // Unit Number used for COM Identification
#define Polled 0
#define TCPCONFIG 7
#define BOOTP_DEBUG		// Allow Dynamic C debugging in bootp.lib
#define BOOTP_VERBOSE		// Print lots of detail
#define DHCP_NUM_SMTP 1		// Get an SMTP server if possible
#define DHCP_NUM_ROUTERS 2	// Get up to 2 routers (gateways) if possible
#define DHCP_NUM_DNS  2		// Get up to 2 DNS (Domain Name System) servers if possible
#define DHCP_NUM_QOTD 2		// Get up to 2 cookie (Quote Of The Day) servers if possible
#define MAX_COOKIES 2		// Also need to tell main tcp lib (default is 1).
#define MAX_UDP_SOCKET_BUFFERS 1
#define LOCAL_PORT	420
#define REMOTE_IP			"255.255.255.255" /*broadcast*/


#define Rth	10000.0									// thermistor T25 resistance
#define Bth 4100.0									// thermistor B value
#define Rex 10000.0									// other resistor
#define ADC_RTC		0		// thermocouple input
#define DAC_RTC		1		// output for thermocouple resistor network
#define CYCLE_TIME 10



#define N_CHANNELS      2
#define DIM_L 10
#define DIM_H 60




#define STATE_INIT	0
#define STATE_STEADY	1
#define MAX_BUFLEN	256
#define INPUT_COOKED
//#undef INPUT_COOKED

#define DELAYTIME 50 //350

#memmap xmem
#use "dcrtcp.lib"



//---------------------------------------------------------
// Macro's
//---------------------------------------------------------
#define MAXDISPLAYROWS	4
#define LEDOFF				0
#define TOGGLE				1
#define INCREMENT			2
#define OPERATE			3

#define ASCII				0
#define NUMBER				1



typedef struct PID	{
		double	SetPoint;         //	Desired Value
      double	Proportion;			//	Proportional Const
		double	Integral;			//	Integral Const
		double	Derivative;			//	Derivative Const
      double	LastError;			//	Error[-1]
		double	PrevError;			//	Error[-2]
		double	SumError;			//	Sums of Errors
      double   Output;				//Output of System
      double 	iMin, iMax;
      double   PTerm;
      double   ITerm;
      double  	DTerm;

}	PID;




//----------------------------------------------------------
// Main_Menu options
//----------------------------------------------------------
// Can insert/delete menu options. The highlight bar is setup
// to start with the first MENU option and stop at the last
// menu option in the MENU.
//
// When adding/deleting menu options you must match up the
// case statements to the menu option number.
//
long settings[6];
   void* save_data[1];
	unsigned int save_lens[1];
float settings_PID[8];
   void* save_data_PID[1];
	unsigned int save_lens_PID[1];

const char *main_menu[] =
{		" <<<<Main Menu>>>>",
		"1)Return to Program",
		"2)Download Data",
		"3)Zero Data Store",
		"4)Calibrate Unit",
		"5)Set Date & Time",
		"6)Calibrate Ana In",
		"7)Calibrate Ana Off",
		NULL
};
const char *treatments[] =
{		"T1C:",
		"CO2:",
      "T2C:",
		NULL
};

		const char *token;
		const char *delim = " ,:/";


//----------------------------------------------------------
// Structures, arrays, variables
//----------------------------------------------------------
fontInfo fi6x8, fi8x10, fi12x16;
windowFrame textWindow;

typedef struct  {
	int data;
	char *ptr;
} fieldupdate;

struct tm CurTime;

char szTime[40];
char szString[20];
const char Days[] = {"SunMonTueWedThuFriSat"};
const char Months[] = {"JanFebMarAprMayJunJulAugSepOctNovDec"};



int ledCntrl;
int beeperTick, timerTick ;
int max_menu_options;
int max_cmds_options;
unsigned long ulTime;
char *keybuffer;






#define BINBUFSIZE 127
#define BOUTBUFSIZE 127
#define MAX_SENTENCE 100


#define TURNON 1
#define TURNOFF 0




typedef unsigned char uchar;
typedef unsigned int  uint;
typedef unsigned long ulong;

static unsigned long store;				// physical memory address to write to



//---------------------------------------------------------------------------
// DEFINIZIONE DELLE VARIABILI
//---------------------------------------------------------------------------
uchar wI;
uchar byIChA[N_CHANNELS+1];
uchar byIChB[N_CHANNELS+1];
uint outd;

uint scan;
uint RECORD;                            //
uint nCont01[N_CHANNELS+1];             //
uint nCont02[N_CHANNELS+1];             //
uint nCont03[N_CHANNELS+1];             //
uint nCont04[N_CHANNELS+1];             //
uint nContao[N_CHANNELS+1];             //
uint LAYER[N_CHANNELS+1];
uint LAYERRELAY[N_CHANNELS+1];

uint nSel;                              //
uint chn;
uint byICh;
uint nI;
uint cnt45;
uint cnt10;
uint bySect;
uint opSect[N_CHANNELS+1];
uint MOBILE;
uint MobDir[9];
uchar T1;                                //
uchar T2;                                //
uchar T3;                                //
uchar T4;                                //
uchar T5;                                //
uchar T6;                                //
uint V1;                                //
uint V2;                                //
uint V3;                                //
uint V4;                                //
uint V5;                                //
int sector;
uint i;
char menudisp;
float fConc[N_CHANNELS+1];
float fDew;
float fTemp;
float fRh;
float fFpro0[N_CHANNELS+1] [DIM_L+1];     //
float fFdif0[N_CHANNELS+1] [DIM_L+1];     //
float fFwin[DIM_L+1];                   //
float fFspro[N_CHANNELS+1];             //
float fFsdif[N_CHANNELS+1];             //
float fFswin[N_CHANNELS+1];             //
float fF10win[DIM_L+1];                 //
float fF10[N_CHANNELS+1];               //
float fVp[N_CHANNELS+1];                //
float fV0[N_CHANNELS+1];                //
float fint0[N_CHANNELS+1];              //
float fVs[N_CHANNELS+1];					//
float fIrgaA;                           //
float fIrgaB;                           //
float fMedIrgaB;                        //
float fFwind;                           //
float fFlow;                            //
float MobSum;                           //
float MobCorr;                          //
float Direz;                            //
float fResA;                            //
float fResB;                            //
float Sumw;                             //
float Sumd;                             //
float f45;
float f10;
float s45;
float s10;

uint day;
uint month;
uint doy;
float dayl;
float sunr;
float suns;
float ora;

float fwind;
float fval[N_CHANNELS+1];
float fmpro[N_CHANNELS+1];
float fmdif[N_CHANNELS+1];
float fmwin[N_CHANNELS+1];
float fm10w[N_CHANNELS+1];
float feint[N_CHANNELS+1];
float fepro[N_CHANNELS+1];
float fedif[N_CHANNELS+1];
float fcor[N_CHANNELS+1];
float fpps[N_CHANNELS+1];
float TARG[N_CHANNELS+1];
float AD_GAIN[N_CHANNELS+1];
float AD_OFFSET[N_CHANNELS+1];
float DA_MULT[N_CHANNELS+1];

float FAINT[N_CHANNELS+1];
float FAPRO[N_CHANNELS+1];
float FADIF[N_CHANNELS+1];
float FCW[N_CHANNELS+1];
float ENDCONO;
float fRet;
float V_OUT_MIN;
float V_OUT_MAX;

float MB;
float fTxlm;
float fMedo;
float fVento;

float medo[N_CHANNELS+1];
float vento[N_CHANNELS+1];
float txlm[N_CHANNELS+1];

uint memPointer;

char ozonator_loc;
char ozonator_rem;
char flow;
char purge;
char inkey;
float tempc;
int purge_off;

char locBuf[50];
char SENTENCE_D[MAX_SENTENCE];
char SENTENCE_C[MAX_SENTENCE];
char SENTENCE_IP[MAX_SENTENCE];
int input_char;
int string_pos_c;
int string_pos_d;
int string_pos_ip;

int backlight;
int timeOn;
int timeDelay = 10;

int StatusCode;
float temptot;                               // variable to sum temp readings
int tempn;

int sec_count;
long off_time[2];
int loc;  //Location Holder for Memory Pointer


struct tm		rtc;		//Time and Date struct
/* vars for telnet recieve daemon */
typedef struct {
	tcp_Socket sock;
	tcp_Socket *s;

	int lport;
	int state;

	char buf[MAX_BUFLEN];
	char cmdbuf[10];
} telnet_recv;

telnet_recv tr_state;
const telnet_recv *const state = &tr_state;
udp_Socket sock;    //Added 113005
char message[250];

	PID			sPID;							//	PID Control Structure
   PID			sPID1;							//	PID Control Structure
   PID			sPID2;							//	PID Control Structure
	double		rOut;							//	PID Response (Output)
	double		rIn;							//	PID Feedback (Input)

void calc_day(void);
void  fControl(void);
void TurnON(void);
void TurnOFF(void);
void readString_IP(void);
void calibrate(int sector);
void cont_loop(void);
float readtemp(int channel );
void minute_average(void);
void second_data(void);
void menu(void);
void keypress(void);
void SetDateTime(void);
void DispMenu(void);
int init_recv(int port);
void recv_tick(void);
void receive_data(char *buf, int len);
float CalcTempSet(void);
void ReadData(void);
//void print_results(void);

int receive_packet_udp(void)
{
	auto int i;
	static char buf[128];

	#GLOBAL_INIT
	{
		memset(buf, 0, sizeof(buf));
	}

	/* receive the packet */
	if (-1 == udp_recv(&sock, buf, sizeof(buf))) {
		/* no packet read. return */
		return 0;
	}


	 for(i=0;i<sizeof(buf);i++)
	 	{
	 	input_char = buf[i];
	 	if(input_char == '\r')
			{
			//printf("Received Return \n");
			SENTENCE_IP[string_pos_ip++] = '\0';
			readString_IP();
			}
		else if(input_char > 0)
			{
			SENTENCE_IP[string_pos_ip] = input_char;
			string_pos_ip++;
			//printf("%d \t %c \n",input_char,input_char);
			}
		}




   memset(buf, 0, sizeof(buf));

	return 1;
}


double PIDCalc(  PID *pp,double NextPoint)
{
	double dError,Error;

		pp->SumError += (Error = pp->SetPoint - NextPoint);
		dError = pp->LastError - pp->PrevError;
		pp->PrevError = pp->LastError;
		pp->LastError = Error;

 		if (pp->SumError > pp->iMax) pp->SumError = pp->iMax;
  		else if (pp->SumError < pp->iMin) pp->SumError = pp ->iMin;

      pp->PTerm = pp->Proportion * Error;
      pp->ITerm = pp->Integral * pp->SumError;
		pp->DTerm = pp->Derivative * dError;
      pp->Output += pp->PTerm + pp->ITerm +  pp->DTerm;
      //printf("%f,%f,%f,%f \n",pp->PTerm, pp->ITerm , pp->DTerm, pp->Output   );
      if (pp->Output < V_OUT_MIN)
			{
				pp->Output = V_OUT_MIN;
			}

		   if (pp->Output > V_OUT_MAX)
			{
				pp->Output = V_OUT_MAX;
         }
	return(pp->Output);
}
void PIDInit(PID *pp)

{     memset ( pp,0,sizeof(PID) );
}

main()
{

   int inputnum;
   int outputnum;
   //loc = 0;

	store = xalloc(40960);//(65536);		// physical memory address (SRAM)

	keyInit();			// Start-up the keypad driver
	keypadDef();		// Use the default keypad ASCII return values
	brdInit();
	glInit();			// Initialize the graphic driver
   digOutConfig(0xFFFF);
ifconfig(IF_DEFAULT,			// (DHCP only works on default interface)
		//IFS_DHCP_TIMEOUT, 60,		// Specify timeout in seconds
      IFS_DHCP_TIMEOUT, 10,		// Specify timeout in seconds
		IFS_DHCP_FALLBACK, 1,	// Allow use of fallbacks to static configuration
		IFS_ICMP_CONFIG, 1,		// Also allow use of directed ping to configure (only if DHCP times out).
		IFS_END);

	sock_init();
//print_results();
	/*
	 * Listen on the port, and otherwise prepare the daemon
 	*/
	if(init_recv(23)) {
		printf("Error in init_recv - couldn't listen on port\n");
		exit(0);
		}
   if(!udp_open(&sock, LOCAL_PORT, resolve(REMOTE_IP), 0, NULL)) {
		printf("udp_open failed!\n");
		exit(0);
      }

   save_data[0] = &settings;
	save_lens[0] = sizeof(settings);
   save_data_PID[0] = &settings_PID;
	save_lens_PID[0] = sizeof(settings_PID);

   	PIDInit ( &sPID );					//	Initialize Structure
      PIDInit ( &sPID1 );					//	Initialize Structure
      PIDInit ( &sPID2 );					//	Initialize Structure


	glBackLight(255);	// Turn-on the backlight
	glXFontInit(&fi6x8, 6, 8, 32, 127, Font6x8);			//	Initialize 6x8 font
	StatusCode = 0;
  	ozonator_loc = 1;
  	ozonator_rem = 1;
	flow =0;     //Must be 1 for ozonator to come on.
   purge = 0;

	serBopen(115200);
	serMode(0);
	memPointer = 0;
	     //----------------------------------------------------------------------
     // Initialize the variables
     //----------------------------------------------------------------------


   nSel=0;
   chn=0;
   V_OUT_MAX=10; //Maximum output voltage at pressure regulator
	V_OUT_MIN=0;  //Minimum output voltage at pressure regulator

   for(i = 0;i < N_CHANNELS+1;i++)
   	{
   	byIChA[i]=0;
		byIChB[i]=0;
		feint[i]=0;
		fepro[i]=0;
		fedif[i]=0;
		}
for(chn=0;chn < N_CHANNELS+1;chn++)
	{

		medo[chn] = 0;
		vento[chn] = 0;
		txlm[chn] = 0;
		nContao[chn] = 0;
	}
	s45=0;
	f45=0;
	cnt45=0;
	s10=0;
	f10=0;
	cnt10=0;
	outd = 0;
   opSect[0] = 0;
   MOBILE=60;    //60;    //Running average for directional control
	MB=10;        //Running average for wind speed
	ENDCONO=60;	//60
	RECORD=0;
   sec_count = 0;

	string_pos_c = 0;
	string_pos_d = 0;
	string_pos_ip = 0;
	SENTENCE_D[0] = '\0';
	SENTENCE_C[0] = '\0';
	SENTENCE_IP[0] = '\0';

   //  Original PID Values if needed.
   settings_PID[0] =0.005;
   settings_PID[1] =0.0;
   settings_PID[2] =0.5;
   settings_PID[3] =0.0001;
   settings_PID[4] =0.0;
   settings_PID[5] =0.0;
   settings_PID[6] =-0.5;
   settings_PID[7] =0.5;
   writeUserBlockArray(25, save_data_PID, save_lens_PID, 1);

	fDew = 0;
   	readUserBlockArray(save_data, save_lens, 1, 0);
      readUserBlockArray(save_data_PID, save_lens_PID, 1, 25);



   /*-----------------------------------------*/
      TARG[0] = (float)CalcTempSet();
      //TARG[0] = settings[0];
		TARG[1] = settings[2];
      TARG[2] = 0;
      FAINT[0]=settings_PID[0];   //Initial=0.00002  6/24  -0.00016,-0.0008  6/25 -0.00006  8/9 -0.00008
		FAPRO[0]=settings_PID[1];     //Initial=0.0008 6/24  -0.0032,-0.0016
   	FADIF[0]=settings_PID[2];      //Initial=0.008
      FAINT[1]=settings_PID[3];   //Initial=0.00002  6/24  -0.00016,-0.0008  6/25 -0.00006  8/9 -0.00008
		FAPRO[1]=settings_PID[4];     //Initial=0.0008 6/24  -0.0032,-0.0016
   	FADIF[1]=settings_PID[5];      //Initial=0.008

      FAINT[2]=0;   //Initial=0.00002  6/24  -0.00016,-0.0008  6/25 -0.00006  8/9 -0.00008
		FAPRO[2]=0;     //Initial=0.0008 6/24  -0.0032,-0.0016
   	FADIF[2]=0;      //Initial=0.008
      sPID.Proportion	= settings_PID[0];			//	Set PID Coefficients
		sPID.Integral		= settings_PID[1];
		sPID.Derivative	= settings_PID[2];
      sPID1.Proportion	= settings_PID[3];			//	Set PID Coefficients
		sPID1.Integral		= settings_PID[4];
		sPID1.Derivative	= settings_PID[5];
      sPID2.Proportion	= 0;			//	Set PID Coefficients
		sPID2.Integral		= 0;
		sPID2.Derivative	= 0;
		sPID.SetPoint     = (float)CalcTempSet();			//	Set PID Setpoint
      sPID1.SetPoint    =  settings[2];
      sPID2.SetPoint    =  0;
      sPID.iMin 			= settings_PID[6];
      sPID.iMax			= settings_PID[7];
      FCW[0]=0.3;          //Initial=0.2
      FCW[1]=0.3;          //Initial=0.2


	LAYER[0] = 0;  // [0]=CO2   [1]=O3   Define this for N_CHANNELS
	LAYER[1] = 1;
   LAYER[2] = 2;

	LAYERRELAY[0] = 6;  //Define which relay board controls each layer
	LAYERRELAY[1] = 5;

	AD_GAIN[0] = 50;
	AD_GAIN[1] = 0;
	AD_OFFSET[0] = 0;
	AD_OFFSET[1] = 0;

	DA_MULT[0] = .5;
	DA_MULT[1] = .5;
	FCW[0]=0.0; //0.5
	FCW[1]=0.0;



/*-----------------------------------------*/

for(nI=0; nI<N_CHANNELS+1;nI++)    // Inizializza  contatori
   	{

      fFspro[nI]=0;
      fFsdif[nI]=0;
      fFswin[nI]=0;
      fint0[nI]=0;
	   nCont01[nI]=1;
	   nCont02[nI]=1;
	   nCont03[nI]=1;
	   nCont04[nI]=1;
	   nContao[nI]=0;
      fV0[nI] = 0; //NEW
	   fVp[nI]= 0; //fV0[nI];
  	   if (fVp[nI]>V_OUT_MAX)
         {
	      fVp[nI]=V_OUT_MAX;
         }
		for(wI=1; wI<=DIM_L;wI++)    // Inizializza  contatori

			{
			fFpro0[nI] [wI]=0;
			fFdif0[nI] [wI]=0;
			fFwin[wI]=0;
			fF10win[wI]=0;
         }
      }
   	 	menudisp=0;
	timeOn = (int)SEC_TIMER;

cont_loop();

}

void cont_loop()
{

	int memo_second;
   int sec_now;


   int Ip;
   float sba1;
   float sba2;


//----------------------------------------------------------------------
//************************   MAIN LOOP    ******************************
//----------------------------------------------------------------------


	while(1)
	{
	recv_tick();
   receive_packet_udp();

	costate
	{
		keyProcess ();
		waitfor(DelayMs(10));
	}

	costate
	{
	waitfor ( inkey = keyGet() );		//	Wait for Keypress
				keypress();

	}

   costate
	{
		TurnOFF ();
		waitfor(DelayMs(10));
	}

	costate
	{

		if(timeOn + timeDelay < (int)SEC_TIMER)
		{
		backlight = 0;
		glBackLight(backlight);
		//printf("%d \n",backlight);

		};

		if (memo_second != (int)SEC_TIMER)
			{
         ledOut(0,!digIn(0));
      	ledOut(1,1); //Flash watch light
         memo_second = (int)SEC_TIMER;
			calc_day();
         	sec_count++;
				if(sec_count >= CYCLE_TIME)
				{
            TurnON();
            }



      	fControl();


         second_data();
         //printf("%d \n",nContao[0]);
         if (nContao[0] == ENDCONO)
         	{
         	minute_average();  //calculate minute averages

				}
			ledOut(1,0);

        	}
      hitwd();
	}
   }


}

float CalcTempSet()
{
long seconds;
float phase;
float tempsetp;
tm_rd(&rtc);


seconds = ((long)rtc.tm_hour*3600) + ((long)rtc.tm_min*60);
phase = sin(((seconds-36000)*PI)/43200);
tempsetp = (((float)settings[0]+(float)settings[1])/2) + ((((float)settings[0]-(float)settings[1])/2)*phase);
//printf("%f %f %f %f %ld ",((settings[0]+settings[1])/2),(((settings[0]-settings[1])/2)*phase),tempsetp, phase, seconds);
return tempsetp;


}




void TurnON()
{
sec_count = 0;
//fVs[1] = 1; //Added to test CO2 stability 01/05/05  TEMPORARY
if(fVs[0] > 0)ledOut(5,1); //Flash watch light
if(fVs[1] > 0)ledOut(6,1); //Flash watch light
if(fVs[0] > 0) digOut(0,1);
if(fVs[1] > 0)digOut(1,1);


off_time[0] = MS_TIMER + (fVs[0]*1000);
off_time[1] = MS_TIMER + (fVs[1]*1000);
//printf("%5.2f, %5.2f \n",   fVs[0],fVs[1]);

}
void TurnOFF()
{
if (MS_TIMER >= off_time[0])
{
ledOut(5,0);
digOut(0,0);
}

if (MS_TIMER >= off_time[1])
{
ledOut(6,0);
digOut(1,0);
}


}


float readtemp(int channel)
{
float R2,R1,V1,V2,A,T;
float a[3],b[3],c[3],t;                                   // variable to count temp readings
a[0] = .0011266252;
b[0] = 2.3450643e-4;
c[0] = 8.640716e-8;
a[1] = .0011266252;
b[1] = 2.3450643e-4;
c[1] = 8.640716e-8;
a[2] = .0011266252;
b[2] = 2.3450643e-4;
c[2] = 8.640716e-8;
//a[0] = 0.0010261734;
//b[0] = 2.3963931E-4;
//c[0] = 1.5456747E-7;

	V1 = 1.0;
	R1 = Rex;
	A = 1/298.0 - ((1/Bth) * log(Rth));			// compute thermistor constant

	anaOutVolts(DAC_RTC, V1); 						// set output voltage for DAC0

   for (tempn=0;tempn<10;tempn++)
   	{
      //printf("%8.2f %d\n", R2,channel);
   	V2 = anaInVolts(channel);    					// read voltage from ADC0
		R2 = V2*R1/(V1-V2);								// compute thermistor resistance
   	if(R2 > 100)
      {
      t = (1 / (a[channel] + (b[channel]*log(R2)) + (c[channel]* log(R2)*log(R2)*log(R2))))-273.15;
      temptot +=  t;
      }
      else
      {
      t = -9999;
      temptot +=  t;
      }
      }
      tempc =   temptot /10 ;
      //printf("%6.2f \n",tempc);
      temptot = 0.0;											// & zero out vars holding

return tempc;
}










/************************************************************/
/*                    fControl                              */
/************************************************************/
void fControl(void)
{
		fpps[0]= readtemp(0);
    	//fpps[0]= 20;
   	fpps[1]= anaInVolts(1)*10000;
      printf("%12.6f \n",fpps[1]);
      fpps[2]= readtemp(2);
      fVp[0] = PIDCalc ( &sPID,fpps[0] );    // Perform PID Interation
      if(digIn(0) && sPID1.SetPoint != 0) fVp[1] = PIDCalc ( &sPID1,fpps[1] );    // Perform PID Interation
      else    //Zero Output if Analyzer is in alarm;
      	{
         fVp[1]=0;
         PIDInit ( &sPID1 );
         sPID1.Proportion	= settings_PID[3];			//	Set PID Coefficients
			sPID1.Integral		= settings_PID[4];
			sPID1.Derivative	= settings_PID[5];
         sPID1.SetPoint = settings[2];
         }

      fVp[2] = PIDCalc ( &sPID2,fpps[2] );    // Perform PID Interation
	for(chn=0;chn < N_CHANNELS+1;chn++)
	{

  		nContao[chn]++;

		fVs[chn]=fVp[chn];






		txlm[chn] = txlm[chn] + fVs[chn];
		medo[chn] = medo[chn] + fpps[chn];
		//vento[chn] = fwind + vento[chn];
	}  //Chiude il loop della notte 18.08.2000


return;
}



void second_data(void)
{
auto int retval1;
	tm_rd(&rtc);
      Direz = (anaInVolts(10)*100);
		sprintf(message,"S,%d,%02d:%02d:%02d,%.2f,%.1f,%.1f,%.2f,%.0f,%.0f,%.2f,%.0f,%.0f,%f,%f,%f \r",UNIT_ID,rtc.tm_hour,rtc.tm_min,rtc.tm_sec,fVs[0],fpps[0],sPID.SetPoint,fVs[1],fpps[1],TARG[1],fVs[2],fpps[2],sPID1.SetPoint,sPID.PTerm,sPID.ITerm,sPID.DTerm);

	if(state->state == 1)
		{
		//for(i=0;i<20;i++){
		retval1 = sock_fastwrite(state->s,message,strlen(message));
		//}
	}

	if(!menudisp)
	{
   glPrintf(0,0, &fi6x8, "%02d/%02d/%04d  %02d:%02d:%02d", rtc.tm_mon,rtc.tm_mday,(1900 + rtc.tm_year),rtc.tm_hour,rtc.tm_min,rtc.tm_sec);
  	glPrintf(0,8, &fi6x8, "%s%4.1f/%4.1f V:%4.1f",treatments[LAYER[0]],fpps[0],sPID.SetPoint, fVs[0]);
	glPrintf(0,16, &fi6x8, "%s%4.0f/%4.0f V:%4.1f",treatments[LAYER[1]],fpps[1],sPID1.SetPoint, fVs[1]);
   glPrintf(0,24, &fi6x8, "%s%4.1f/%4.1f V:%4.1f",treatments[LAYER[2]],fpps[2],sPID2.SetPoint, fVs[2]);


	}
}






//*************************************************************************************************************************************************************************************************
//******    Minute averages
//*************************************************************************************************************************************************************************************************
void minute_average(void)
{
auto int retval1;
for(chn=0;chn < N_CHANNELS+1;chn++)
	{
		txlm[chn] = txlm[chn] / nContao[chn];
		vento[chn] = vento[chn] / nContao[chn];
		medo[chn] = medo[chn] / nContao[chn];
	}
		//fDew = fDew/nContao[0];

		(int)StatusCode = ozonator_loc && ozonator_rem && flow;
		sprintf(message,"M,%d,%02d/%02d/%04d,%02d:%02d:%02d,%.2f,%.1f,%.1f,%.2f,%.1f,%.1f,%.2f,%.1f,%.1f,%d \r",UNIT_ID,rtc.tm_mon,rtc.tm_mday,(1900 + rtc.tm_year),rtc.tm_hour,rtc.tm_min,rtc.tm_sec,txlm[0],medo[0],sPID.SetPoint,txlm[1],medo[1],sPID1.SetPoint,txlm[2],medo[2],TARG[2],StatusCode);
      if(state->state == 1)
      	{
	      retval1 = sock_fastwrite(state->s,message,strlen(message));
	      }

 if(loc >= 35879) loc = 0;    //60455

      root2xmem(store+loc*4,&SEC_TIMER,4);//Store Time Stamp at beginning of each loop
   	loc++;



      root2xmem(store+loc*4, &txlm[1], 4);    //txlm[0],medo[0],sPID.SetPoint
   	loc++;
      root2xmem(store+loc*4, &medo[1], 4);    //txlm[0],medo[0],sPID.SetPoint
      loc++;
      root2xmem(store+loc*4, &sPID1.SetPoint, 4);    //txlm[0],medo[0],sPID.SetPoint
      loc++;
      //Store 2 temps
      root2xmem(store+loc*4, &medo[0], 4);    //txlm[0],medo[0],sPID.SetPoint
      loc++;
      root2xmem(store+loc*4, &medo[2], 4);    //txlm[0],medo[0],sPID.SetPoint
      loc++;


   printf("%d line 958\n", loc);



        	if(RECORD > 2975) RECORD=0;
        	//write_mem(RECORD);
        	RECORD = RECORD + 1;

for(chn=0;chn < N_CHANNELS+1;chn++)
	{

		medo[chn] = 0;
		vento[chn] = 0;
		txlm[chn] = 0;
		nContao[chn] = 0;
	}
		fDew = 0;
sPID.SetPoint = (float)CalcTempSet();
//TARG[0] = settings[0];

}


void calc_day(void)
{
      month=rtc.tm_mon;
		day=rtc.tm_mday;
	   	  if(month==1) { doy = day;}
			  if(month==2) { doy = 31+ day;}
	        if(month==3) { doy = 59+ day;}
	        if(month==4) { doy = 90+ day;}
	        if(month==5) { doy = 120+ day;}
	        if(month==6) { doy = 151+ day;}
	        if(month==7) { doy = 181+ day;}
	        if(month==8) { doy = 212+ day;}
	        if(month==9) { doy = 243+ day;}
	        if(month==10) { doy = 273+ day;}
	        if(month==11) { doy = 304+ day;}
			  if(month==12) { doy = 334+ day;}

	dayl= 10.14691451-0.005717757*doy+0.0007912*doy*doy-4.46401E-06*doy*doy*doy+6.4177E-09*doy*doy*doy*doy;

           sunr= 12-dayl/2;
           suns= 12+dayl/2;
           ora=rtc.tm_hour+(float)(rtc.tm_min/60.);


}


/************************************************************/
/*                    Calibrate                             */
/************************************************************/
void calibrate(int sector)
{


}





void keypress(void)
{
printf("Key Pressed \n");

	if((int)backlight == 0)
		{
		printf("Key Pressed - Light On \n");

		backlight = 1;
		glBackLight(backlight);
		printf("%d \n", backlight);
		timeOn = (int)SEC_TIMER;
		return ;
		}
switch (inkey)
			{
				case 'E':
					menudisp=0;
					DispMenu();
					break;

				default:

					break;
			}

}


//------------------------------------------------------------------------
// Milli-sec delay function
//------------------------------------------------------------------------
nodebug
void msDelay(long sd)
{
	auto unsigned long t1;

	t1 = MS_TIMER + sd;
	while ((long)(MS_TIMER-t1) < 0);
}


//------------------------------------------------------------------------
// Process key to do number and ASCII field changes
//------------------------------------------------------------------------
int ProcessKeyField(int mode, fieldupdate *field)
{
	static int wKey;

	keyProcess();
	msDelay(100);
	if((wKey = keyGet()) != 0)
	{
		switch(wKey)
		{
			// Decrement number by 10 or pointer by 3
			case '-':
				if(mode == NUMBER)
					field->data -= 10;
				else
					field->ptr  -= 3;
				break;

			// Increment number by 10 or pointer by 3
			case '+':
				if(mode == NUMBER)
					field->data += 10;
				else
					field->ptr  += 3;
				break;

			// Increment number or pointer by 1
			case 'U':
				if(mode == NUMBER)
					field->data++;
				else
					field->ptr++;
				break;

			// Decrement number or pointer by 1
			case 'D':	// Decrement X1
				if(mode == NUMBER)
					field->data--;
				else
					field->ptr--;
				break;

			// Done Editing field
			case 'E':
				wKey = 'E';
				break;

			default:
				wKey = -1;
		  		break;
		}
	}
	return(wKey);
}


//------------------------------------------------------------------------
// Get and process the users MENU option
//------------------------------------------------------------------------
int GetKeypadOption( int *offset, int *highlight, int msize )
{
	static int wKey;

	if((wKey = keyGet()) != 0)
	{
		switch(wKey)
		{
			case '-':	// Page down
				if(*offset < (((msize)/sizeof(int)) - 1))
				{
					if((*offset + MAXDISPLAYROWS) < (((msize)/sizeof(int)) - 1))
						*offset += 4;
				}
				if(*offset == 0)
					*highlight = 1;
				else
					*highlight = 0;
				wKey = -1;
				break;

			case '+':	// Page up
				if(*offset > 3)
					*offset -=4;
				else
					*offset = 0;
				if(*offset == 0)
					*highlight = 1;
				else
					*highlight = 0;
				wKey = -1;
				break;

			case 'U':	// Scroll-up by one line
				*highlight -= 1;
				if(*highlight < 0)
				{
					*offset -= 1;
					*highlight = 0;
				}
				if(*offset == 0 && *highlight == 0)
					*highlight = 1;
				wKey = -1;
				break;

			case 'D':	// Scroll-down by one line
				if((*offset + (*highlight) + 1) < (((msize)/sizeof(int)) - 1))
				{
					*highlight += 1;
					if(*highlight > 3)
					{
						*offset += 1;
						*highlight = 3;
					}
				}
				wKey = -1;
				break;

			case 'E':	// Select option
				wKey = *offset + *highlight;
				break;

			default:
				wKey = -1;
		  		break;
		}
	}
	return(wKey);
}

//------------------------------------------------------------------------
// Display a MENU on the LCD display and get the menu option from the user
//------------------------------------------------------------------------
int display_menu ( char **line, int initialize, int menusize)
{
	static int offset, tmpoffset, i;
	static int menu_option;
	static int lasthighlight;
	static int scrolling;
	static int highlight;

	costate
	{
		if(initialize)
		{
			offset = 0;				// Initialize menu line index
			highlight = 1;			// Assumes all menus have a heading
			tmpoffset = ~offset;
		}

		menu_option = 0;			// Initially set to no option selected
		scrolling = FALSE;

		// Wait until you get a valid user option
		while (menu_option == 0)
		{
			// Display menu option
			if(tmpoffset != offset)
			{
				glBlankScreen();
				for(i=0; i < 4; i++)
				{	// Display up to 4 lines of menu options
					TextGotoXY(&textWindow, 0, i);
					TextPrintf(&textWindow, "%s", line[offset]);
					if (line[offset + 1] == NULL) {
			 			break;
					}
					offset++;
				}

				// Reset the offset back to the first option displayed
				offset = offset-i;
				tmpoffset = offset;
			}
			glSetBrushType(PIXXOR);
			glBlock (0, highlight*8, 122, 8);
			glSetBrushType(PIXBLACK);
			lasthighlight = highlight;


			// Get the user's option
			waitfor((menu_option = GetKeypadOption(&offset, &highlight, menusize)));
			// Check if user selected the scrolling option

			glSetBrushType(PIXXOR);
			glBlock (0, lasthighlight*8, 122, 8);
			glSetBrushType(PIXBLACK);
			if (menu_option == -1)
			{

				// Set menu option to zero due to scrolling operation
				menu_option = 0;
				scrolling = TRUE;
			}
		}
	}
	tmpoffset = offset;
	return(menu_option);
}

//------------------------------------------------------------------------
// Format the Date and Time for the LCD display
//------------------------------------------------------------------------
void FormatDateTime ( void )
{	char Day[4], Mon[4];

	ulTime = read_rtc ();			// get the RTC value
	mktm( &CurTime, ulTime );		// convert seconds to date values

	strncpy ( Day, &Days[CurTime.tm_wday*3], 3 );
	strncpy ( Mon, &Months[(CurTime.tm_mon-1)*3], 3 );
	Day[3] = 0;
	Mon[3] = 0;

	sprintf ( szTime, "%s %s %d, %d \n%d:%02d:%02d",
		Day, Mon, CurTime.tm_mday, CurTime.tm_year+1900,
		CurTime.tm_hour, CurTime.tm_min, CurTime.tm_sec );
}

//------------------------------------------------------------------------
// Date and Time prompt message routine
//------------------------------------------------------------------------
void date_prompt(char *ptr, int *col, int *row)
{
	glBlankScreen();
	TextGotoXY(&textWindow, 0, 0);
	TextPrintf(&textWindow, "%s", ptr);
	TextCursorLocation(&textWindow, col, row);

	TextGotoXY(&textWindow, 0, 3);
	TextPrintf(&textWindow, "ENTER to Continue...");
}


//------------------------------------------------------------------------
// Set Date and Time
//------------------------------------------------------------------------
void SetDateTime( void )
{
	int wKey;
	int col, row;
	char buffer[256];
	fieldupdate dateTime;

	// Setup for FAST key repeat after holding down key for 12 ticks
	keyConfig (  6,'E',0, 12, 1,  1, 1 );
	keyConfig (  2,'D',0, 12, 1,  1, 1 );
	keyConfig (  5,'+',0, 12, 1,  1, 1 );
	keyConfig (  1,'U',0, 12, 1,  1, 1 );
	keyConfig (  4,'-',0, 12, 1,  1, 1 );
	tm_rd(&CurTime);
	date_prompt("Select \n4 digit year: ", &col, &row);
	dateTime.data = (rtc.tm_year+1900);
	while(1)
	{
		sprintf(buffer, "%04d", dateTime.data);
		TextGotoXY(&textWindow, col, row);
		TextPrintf(&textWindow, "%s", buffer);
		while((wKey = ProcessKeyField(NUMBER, &dateTime)) == 0);
		if(dateTime.data < 1900 || dateTime.data > 2047)
		{
			dateTime.data = (1900 + rtc.tm_year);
		}
		if(wKey == 'E')
		{
			if( dateTime.data  >= 1900 && dateTime.data < 2048) {
				CurTime.tm_year = dateTime.data - 1900;	// offset from 1900
				break;
			}
		}
	}

	date_prompt("Enter month: ", &col, &row);
	dateTime.data = rtc.tm_mon;
	while(1)
	{
		sprintf(buffer, "%02d", dateTime.data);
		TextGotoXY(&textWindow, col, row);
		TextPrintf(&textWindow, "%s", buffer);
		while((wKey = ProcessKeyField(NUMBER, &dateTime)) == 0);
		if(wKey == 'E')
		{
			if( dateTime.data >= 1 && dateTime.data < 13 )
			{
				CurTime.tm_mon = dateTime.data;
				break;
			}
		}
		if(dateTime.data < 1 || dateTime.data > 12)
		{
			dateTime.data  = (dateTime.data < 1) ? 12 : 1;
		}
	}

	date_prompt("Enter \nday of month: ", &col, &row);
	dateTime.data = rtc.tm_mday;
	while(1)
	{
		sprintf(buffer, "%02d", dateTime.data);
		TextGotoXY(&textWindow, col, row);
		TextPrintf(&textWindow, "%s", buffer);
		while((wKey = ProcessKeyField(NUMBER, &dateTime))== 0);
		if(wKey == 'E')
		{
			if( dateTime.data  >= 1 && dateTime.data < 32) {
				CurTime.tm_mday = dateTime.data;
				break;
			}
		}
		if(dateTime.data < 1 || dateTime.data > 31)
		{
			dateTime.data  = (dateTime.data < 1) ? 31 : 1;
		}
	}


	date_prompt("Enter \nhour (24hr): ", &col, &row);
	dateTime.data = rtc.tm_hour;
	while(1)
	{
		sprintf(buffer, "%02d", dateTime.data);
		TextGotoXY(&textWindow, col, row);
		TextPrintf(&textWindow, "%s", buffer);
		while((wKey = ProcessKeyField(NUMBER, &dateTime)) == 0);
		if(wKey == 'E')
		{
			if(dateTime.data >= 0 && dateTime.data < 24) {
				CurTime.tm_hour = dateTime.data;
				break;
			}
		}
		if(dateTime.data < 0 || dateTime.data > 23)
		{
			dateTime.data  = (dateTime.data < 0) ? 23 : 0;
		}
	}

	date_prompt("Enter minute: ", &col, &row);
	dateTime.data = rtc.tm_min;
	while(1)
	{
		sprintf(buffer, "%02d", dateTime.data);
		TextGotoXY(&textWindow, col, row);
		TextPrintf(&textWindow, "%s", buffer);
		while((wKey = ProcessKeyField(NUMBER, &dateTime)) == 0);
		if(wKey == 'E')
		{
			if( dateTime.data >= 0 && dateTime.data < 60) {
				CurTime.tm_min = dateTime.data;
				break;
			}
			if(wKey == 'E')
			{
				break;
			}
		}
		if(dateTime.data < 0 || dateTime.data > 59)
		{
			dateTime.data  = (dateTime.data < 0) ? 59 : 0;
		}
	}

	CurTime.tm_sec = 0;

	tm_wr(&CurTime);
	SEC_TIMER = mktime(&CurTime);


	//ulTime = mktime ( &CurTime );		// get seconds from 1/1/1980
	//write_rtc ( ulTime );				// set the real time clock
	keypadDef();

	glBlankScreen();
	while(1)
	{
		// Get current Date/Time
		FormatDateTime();					// convert to text

		// Display Date and Time
		glBuffLock();
		TextGotoXY(&textWindow, 0, 0);
		TextPrintf(&textWindow, "%s\n", szTime);

		// Display user exit message
		TextGotoXY(&textWindow, 0, 3);
		TextPrintf(&textWindow, "Press Key to EXIT    ");
		glBuffUnlock();

		keyProcess ();
		if((wKey = keyGet()) != 0)
		{
			glBlankScreen();
			break;
		}
	}
}



//------------------------------------------------------------------------
// Sample program to demonstrate the LCD and keypad
//------------------------------------------------------------------------
void DispMenu (	void	)
{
	 int option, initialize;

	//------------------------------------------------------------------------
	// Initialize the controller
	//------------------------------------------------------------------------



	// Setup and center text window to be the entire display
	TextWindowFrame(&textWindow, &fi6x8, 1, 0, 121, 32);

	// Set variables to known states
	initialize = TRUE; 	// Set flag for MENU options to be displayed
	ledCntrl = LEDOFF;	// Initially disable the LED's
	//------------------------------------------------------------------------
	// Main program loop for the MENU system
	//------------------------------------------------------------------------
	for (;;)
	{
		costate
		{
			keyProcess ();
			waitfor(DelayMs(10));
		}

		costate
		{
			// Display the MAIN MENU
			waitfor((option = display_menu(main_menu, initialize,sizeof(main_menu))) > 0);

			// Get menu option from the user
			switch(option)
			{
				// Return
				case 1:  glBlankScreen();
							cont_loop();
				// Turn Ozone ON
				case 2:	glBlankScreen();
                     ReadData();
							cont_loop();
							break;

				// Turn Ozone OFF
				case 3:	glBlankScreen();
							loc = 0;
							cont_loop();
							break;

				// Calibrate Unit
				case 4:	glBlankScreen();
							sector = 0;
							calibrate((int)sector);
							break;

				// Change Date/Time
				case 5:	glBlankScreen();
							SetDateTime();
							initialize = TRUE;
							break;

				// Display current Date/Time
				case 6:	glBlankScreen();
							break;

				// Turn Backlight OFF
				case 7:
							break;


				// User made invalid selection
				default:
					break;
			}
		}
	}
}


/* init the socket */
int init_recv(int port)
{
	state->s = &state->sock;
	state->lport = port;
	tcp_listen(state->s, port, 0, 0, NULL, 0);
	state->state = STATE_INIT;
	return 0;
}

#ifdef INPUT_COOKED
void cook_cmd(void)
{
	auto int len;
	len = 3;

	while(len > 0) {
		len -= sock_fastwrite(state->s, state->cmdbuf + 3 - len, len);
	}
}

int cook_input(int len)
{
	auto int newlen, i;

	newlen = len;
	for(i=0; i<(len-2); i++) {
		if(state->buf[i] == 255) {
			/* controll code */
			switch(state->buf[i + 1]) {
			case 251:
			case 252: {
				sprintf(state->cmdbuf, "%c%c%c",
					255, 254, state->buf[i + 2]);
				cook_cmd();
				memcpy(state->buf + i, state->buf + i + 3, len - (i + 3));
				newlen -= 3;
				break;
			}
			case 253:
			case 254:
				sprintf(state->cmdbuf, "%c%c%c",
					255, 252, state->buf[i + 2]);
				cook_cmd();
				memcpy(state->buf + i, state->buf + i + 3, len - (i + 3));
				newlen -= 3;
				break;

			case 255:
				break;

			default:
				/* unknown command; kill it */
				memcpy(state->buf + i, state->buf + i + 2, len - (i + 2));
				newlen -= 2;
				break;
			}
		}
	}

	return newlen;
}
#endif

void recv_tick(void)
{
	auto int retval;

	tcp_tick(state->s);

	switch(state->state) {
	case STATE_INIT:
		if(sock_established(state->s)) {
			printf("Connection Established.\n");
			state->state = STATE_STEADY;
		}
		break;

	case STATE_STEADY:
		if(!sock_established(state->s)) {
			/* connection died; reset */
			printf("Connection lost.\n\n");
			init_recv(state->lport);
			break;
		}

		retval = sock_fastread(state->s, state->buf, MAX_BUFLEN);
		if(retval) {
			/* we got data */
#ifdef INPUT_COOKED
			retval = cook_input(retval);
#endif
			receive_data(state->buf, retval); /* give it to the user */
		}
		break;

	default:
		/* shouldn't ever get here */
		/* reset the conroller */
		exit(-1);
	}
}


void receive_data(char *buf, int len)
{
	/*
	 * this is a user-function that will recieve the data
	 * as it comes in. (buf points to the buffer, len is the
	 * length of the data that was received.)
	 *
	 * Note - When this function returns, the buffer will be
	 * overwritten, so if you want the data, it should be
	 * coppied out of the buffer before the function returns.
	 *
	 * Nothing is done with it for now; it is just dropped on
	 * the floor.
	 */

	 auto int i;
	 for(i=0;i<len;i++)
	 	{
	 	input_char = buf[i];
	 	if(input_char == '\r')
			{
			//printf("Received Return \n");
			SENTENCE_IP[string_pos_ip++] = '\0';
			readString_IP();
			}
		else if(input_char > 0)
			{
			SENTENCE_IP[string_pos_ip] = input_char;
			string_pos_ip++;
			//printf("%d \t %c \n",input_char,input_char);
			}
		}
}


void readString_IP(void)
{
		int i;
      auto int retval1;
		printf("%s \n",SENTENCE_IP);
		token = strtok(SENTENCE_IP,delim);

		switch(*token) // Read Command
		{

			case 67: //Calibrate
				string_pos_ip = 0;
				token = strtok(NULL,delim);
				//printf("%d \n",atoi(token));
				calibrate(atoi(token));
			break;

			case 68: //Download
				printf("Download \n");
				string_pos_ip = 0;
				//download(RECORD);
			break;

         case 71: //Get Settings
         printf("Get Settings \n");
         //sprintf(message,"G,0,30,20,550,350,80,80\r");
         sprintf(message,"G,0,%ld,%ld,%ld,%ld,%ld,%ld\r", settings[0], settings[1], settings[2], settings[3], settings[4], settings[5]);
  			if(state->state == 1)
				{
      			retval1 = sock_fastwrite(state->s,message,strlen(message));
  				}

         break;

         case 72: //Get PID Settings
         printf("Get Settings \n");
         //sprintf(message,"G,0,30,20,550,350,80,80\r");
         sprintf(message,"H,0,%f,%f,%f,%f,%f,%f,%f,%f \r", sPID.Proportion, sPID.Integral, sPID.Derivative, sPID1.Proportion, sPID1.Integral, sPID1.Derivative, sPID.iMin, sPID.iMax);
  			if(state->state == 1)
				{
      			retval1 = sock_fastwrite(state->s,message,strlen(message));
  				}
         break;
         case 73: //Save PID Values
         	string_pos_ip = 0;
				token = strtok(NULL,delim);
            token = strtok(NULL,delim);
            settings_PID[0] = atof(token);
            token = strtok(NULL,delim);
            settings_PID[1] = atof(token);
				token = strtok(NULL,delim);
            settings_PID[2] = atof(token);
				token = strtok(NULL,delim);
            settings_PID[3] = atof(token);
				token = strtok(NULL,delim);
            settings_PID[4] = atof(token);
            token = strtok(NULL,delim);
            settings_PID[5] = atof(token);
            token = strtok(NULL,delim);
            settings_PID[6] = atof(token);
            token = strtok(NULL,delim);
            settings_PID[7] = atof(token);
            save_data_PID[0] = &settings_PID;
				save_lens_PID[0] = sizeof(settings_PID);

            writeUserBlockArray(25, save_data_PID, save_lens_PID, 1);

            FAINT[0]=settings_PID[0];   //Initial=0.00002  6/24  -0.00016,-0.0008  6/25 -0.00006  8/9 -0.00008
				FAPRO[0]=settings_PID[1];     //Initial=0.0008 6/24  -0.0032,-0.0016
   			FADIF[0]=settings_PID[2];      //Initial=0.008
      		FAINT[1]=settings_PID[3];   //Initial=0.00002  6/24  -0.00016,-0.0008  6/25 -0.00006  8/9 -0.00008
				FAPRO[1]=settings_PID[4];     //Initial=0.0008 6/24  -0.0032,-0.0016
   			FADIF[1]=settings_PID[5];      //Initial=0.008
            sPID.Proportion	= settings_PID[0];			//	Set PID Coefficients
				sPID.Integral		= settings_PID[1];
	  			sPID.Derivative	= settings_PID[2];
     		 sPID1.Proportion	= settings_PID[3];			//	Set PID Coefficients
				sPID1.Integral		= settings_PID[4];
				sPID1.Derivative	= settings_PID[5];
      		sPID2.Proportion	= 0;			//	Set PID Coefficients
				sPID2.Integral		= 0;
				sPID2.Derivative	= 0;
            sPID.iMin = settings_PID[6];
            sPID.iMax = settings_PID[7];


         break;

         case 80:
         	string_pos_ip = 0;
				token = strtok(NULL,delim);
            token = strtok(NULL,delim);
            settings[0] = atoi(token);
            token = strtok(NULL,delim);
            settings[1] = atoi(token);
				token = strtok(NULL,delim);
            settings[2] = atoi(token);
				token = strtok(NULL,delim);
            settings[3] = atoi(token);
				token = strtok(NULL,delim);
            settings[4] = atoi(token);
            token = strtok(NULL,delim);
            settings[5] = atoi(token);
            save_data[0] = &settings;
				save_lens[0] = sizeof(settings);

            writeUserBlockArray(0, save_data, save_lens, 1);
            	TARG[0] = (float)CalcTempSet();
					TARG[1] = settings[2];
               sPID.SetPoint     = (float)CalcTempSet();			//	Set PID Setpoint
      			sPID1.SetPoint    =  settings[2];
      			sPID2.SetPoint    =  0;


         break;


         case 82:   //Reset Controller (R)

            token = strtok(NULL,delim);
               if (atoi(token) == UNIT_ID)
               {
               exit(0);
               }
         break;


			case 84: //Set Time
				//printf("Set Time \n");
				string_pos_ip = 0;
				token = strtok(NULL,delim);
				rtc.tm_mon = atoi(token);	//set month
				token = strtok(NULL,delim);
				rtc.tm_mday = atoi(token); //set day
				token = strtok(NULL,delim);
				rtc.tm_year = (atoi(token)-1900);	//set year
				token = strtok(NULL,delim);
				rtc.tm_hour = atoi(token); //set hour
				token = strtok(NULL,delim);
				rtc.tm_min = atoi(token); //set minute
				token = strtok(NULL,delim);
				rtc.tm_sec = atoi(token); //set second

				tm_wr(&rtc);
				SEC_TIMER = mktime(&rtc);
				sprintf(message,"T,%02d/%02d/%04d,%02d:%02d:%02d \r",rtc.tm_mon,rtc.tm_mday,(rtc.tm_year+1900),rtc.tm_hour,rtc.tm_min,rtc.tm_sec);
						serBputs(message);
   					while (serBwrFree() != BOUTBUFSIZE) ;

			break;

			case 83: //Transmit second data (S)
				string_pos_ip = 0;
				token = strtok(NULL,delim);

					switch(atoi(token))
					{
					case UNIT_ID:
						sprintf(message,"S,%d,%02d/%02d/%04d,%02d:%02d:%02d%5.2f,%5.0f,%.3f,%.3f,%.3f,%4.1f,%4.0f,%d \r",UNIT_ID,T5,T4,(1900 + T6),T1,T2,T3,fVp[chn],fpps[chn],feint,fepro,fedif,fFwind,Direz,opSect[0]);
						serBputs(message);
   					while (serBwrFree() != BOUTBUFSIZE) ;

					}
			break;

			default:


		}
		string_pos_ip = 0;
}


void ReadData(void)
{
int j, l, m;
float a, data[16];
long time, b;
char message[300];
char c[20];
m=0;

for(j=0; j< (loc/6);j++)
	{

	xmem2root(&b, store+m*4, 4);
	mktm(&rtc,b);
	m++;

	for(l=0;l<5;l++)
		{
		xmem2root(&a, store+m*4, 4);
		m++;
		data[l] = a;
		}
		sprintf(message,"%02d/%02d/%04d,%02d:%02d:%02d, %6.3f,%6.1f,%6.1f,%6.3f,%6.3f \n\r", rtc.tm_mon,rtc.tm_mday,(rtc.tm_year+1900),rtc.tm_hour,rtc.tm_min,rtc.tm_sec, data[0], data[1], data[2], data[3], data[4]);
		serBputs(message);
   		while (serBwrFree() != BOUTBUFSIZE) ;
     printf("%02d/%02d/%04d,%02d:%02d:%02d, %6.3f,%6.1f,%6.1f,%6.3f,%6.3f \n", rtc.tm_mon,rtc.tm_mday,(rtc.tm_year+1900),rtc.tm_hour,rtc.tm_min,rtc.tm_sec, data[0], data[1], data[2], data[3], data[4]);


	}

}

