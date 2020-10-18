# Multiple Error Message From single Validation VeeValidate in VueJS
Solution for returning multiple type of error messages from single validation in VeeValidate Validations in VueJS


Method:

//validation for percentage


	Vue.use(VeeValidate);
	
	
	VeeValidate.Validator.extend('percentage', {
	getMessage: (field,params,data) => {
		if(data.message)
		{
			return data.message;
		}
	},
	validate: value => {
		if(Number(value)>=0 && Number(value)<=100)
		{
			if(value.indexOf('.')!=-1)
			{
				if(value.split('.')[1].length<=2)
				{
					return true;
				}
				else
				{
					//error message type 1
					return {data: { message: `Percentage can be entered upto only 2 decimal places` } };
				}
			}
			else
			{
				return true;
			}
		}
		else
		{
			//error message type 2
			return {data: { message: `Percentage should strictly be a number equal to or between 0 and 100` } };
		}  
	}
  	});
